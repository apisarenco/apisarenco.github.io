---
title: "Data Schema For The Win"
subtitle: "Creating projects that only seem complex"
date: 2022-08-08T01:42:43+01:00
draft: false
slug: data-schema-for-the-win
summary: ""
categories:
    - Development
    - Data
tags:
    - data
    - schema
    - nosql
description: |
    Acknowledge and document the data schema at the software architecture level, and you'll have a much smoother application development experience.
---

I started off my career in data with relational databases. 18 years ago I've read 10 pages on how to use Microsoft Access, and my eyes sparkled with enthusiasm, as I was imagining how most of the problems that I, as a "techy boy" encountered at different people who were using mostly Excel for things that it wasn't designed to do.

This quickly turned into a 3-month project, where I, an 18 year old teenager, replaced one of the most labour-intensive and error-prone data entry tasks in Excel, with a new MS Access database + front-end and reporting. Decreased operation time from about 20h per month, to just 4h per month, with no need to retroactively fix wrong reports due to manual errors being discovered weeks after those reports were printed and signed.

**It is in use to this very day 18 years later.** There is an IT department which takes care that MS Access works properly on each machine that they manage. I would be horrified today at the code that I wrote then, and how I wrote it. But it works. And nothing has replaced it. It is a **reliable, final** project.

This event shaped my career. It taught me very early and very quickly that as soon as you define your schema, and validate your data according to consistency rules, things will just work down the line. Back then I didn't even understand these words by the way.

### Excel is not a database

It also doesn't have any schema. Despite it representing tabular data, it is as far away from relational databases as MongoDB would be.

As a data engineer I've had to automate a ton of businesses and departments which were getting swamped by Excel, which wasn't good at reliably producing the same reports as before.

It always starts off with this:

> Excel is easy! I'll just put some data here and there and everywhere, as there's no schema, no constraints, I can do what I want.

Does that sound familiar?

### GIGO

... or as my partner-in-crime likes to say: *"Shit goes in, fancy shit goes out"*. If at the point of ingress you're already getting really bad data, that doesn't conform to a fairly strict schema, the majority of the work is going to be in fitting it into some schema.

### The modern "schemaless" approach

Same as the situation described above with Excel, some software developers will be tempted to start developing software without any thought to schema.

> I'll just persist whatever data I have

... said the developer. Without having to worry about schema definition, schema changes and migrations, the developer adds the data.

The journey begins...

`v1:`
```json
{
    "name": "Joe Flannigan"
}
```

Bob decides to also keep first name and last name, but keeps `name` for backwards compatibility.

`v2:`
```json
{
    "name": "Joe Flannigan",
    "firstName": "Joe",
    "lastName": "Flannigan"
}
```

Uwe thinks that it would be nice to have e-mail there as well, as long with other personal data:

`v3:`
```json
{
    "name": "Marry Flannigan",
    "firstName": "Marry",
    "lastName": "Flannigan",
    "personalDetails": {
        "email": "marry-flannigan@email.corp",
        "birthday": "2003-05-26",
        "gender": "other",
        "address": {
            "streetName": "14th street",
            "houseNumber": "4",
            "unit": "16"
        }
    }
}
```

Charlotte thinks that `address` shouldn't be part of the person details, so she changes it to a reference, because she's also aware that in other databases people use Foreign Keys. Also she removes `name` because it's already possible to deduce it from `firstName` and `lastName`.

`v4:`
```json
{
    "firstName": "Marry",
    "lastName": "Flannigan",
    "personalDetails": {
        "email": "marry-flannigan@email.corp",
        "birthday": "2003-05-26",
        "gender": "other",
        "addressId": "01234567-0123-0123-0123-012345678901"
    }
}
```

But now, everybody is screwed.
* `v1` to `v3` consumers may rely on `name` being present. They could update their apps to use `firstName` and `lastName`, but older data doesn't have those fields, and there's no schema migration script to change it, since there's no schema.
* `v3` relied on address being specified per-person. Writing migration code to get from `v3` to `v4` without data loss would be an undertaking.

The reality is that all of the data products involved with this are going to have to carry legacy code to deal with legacy "schema" that was never intended to be a schema.

There will probably be hardcoded classes which will map mandatory fields in these documents, and will ensure that every value corresponds to validation rules and that lookups work.

There will be custom code that changes every entity one by one, with no regard to locking the record before changing it.

Just ... admit it, there is a schema. The problem is that its acknowledgement was avoided, and thus it created **technical debt**.

### So what's the solution?

Well, sorry for sounding boring, but RDBMS is the proven solution. I'm not saying that you should be stuck in the 80s way of doing things. You can start off with nothing, with just a simple schema, and transition from there.

Make sure that every schema change is documented through a script that does this change, and brings it from `v1` to `v2` for example.

* the data will all have the exact same structure, old and new
* any structure changes that disagree with the data, will not be possible. You won't get errors down the line, you'll see them immediately
* the history of the schema changes is recorded in version control
* you can trust the data that is constrained to a schema. There are no surprises

You don't even have to do any of this manually, and likely you don't even have to write a single line of SQL. With modern ORMs, you just focus on the code.

Since I avoid working with ORMs, I don't know too much about the infrastructure, but the last time I did have to work with [Alembic](https://flask-alembic.readthedocs.io/en/stable/) for Flask, in Python. And it did exactly what I described, reliably and well. There's similar frameworks in most platforms, as [my 2-minute search showed in the case of .NET Core](https://www.reddit.com/r/dotnet/comments/ajqn0r/migrations_for_dapper/).

Acknowledge and document the data schema at the software architecture level, and you'll have a much smoother application development experience.
