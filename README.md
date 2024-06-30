# @jrkienle's TypeScript Monorepo

A monorepo for all of my TypeScript projects

## 👋 Introduction

Hey there! This repo is home to all of my currently in progress, public TypeScript projects. If
anything here gets big enough I might move it to its own repo/org, but I'm not counting on that.
Feel free to dig through anything in here, but please don't expect any official support as these
projects are mostly experiments that I do in my free time. With that in mind, enjoy!

## License

Everything in this repo is licensed under the MIT license. If you either don't know what that means
or really want to dig into the license for whatever reason, check out [LICENSE.md](LICENSE.md).

## Prerequisites

The following prerequisites are **required** to develop with this repo:

- [Bun](https://bun.sh/)

The following prerequisites are optional, but highly recommended:

- [Zed](https://zed.dev/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

## Setup

Once you've installed the above prerequisites, run through the following steps to get everything
set up for local development:

- Clone the repo (`$ git clone ssh://git@github.com:jrkienle/ts-monorepo.git`)
- CD into the repo (`$ cd ./ts-monorepo`)
- Install dependencies (`$ bun install`)

## Code Guidelines

This repo follows my own set of very strict code standards with the goal of having as many of these
standards automated and linter-enforceable as possible. These standards are designed around my
personal workflow and help me to write better, cleaner code, and some of them are definitely
designed around "this feels right" rather than "this is supported by data". These standards can be
found in [CODE_GUIDELINES.md](./CODE_GUIDELINES.md).
