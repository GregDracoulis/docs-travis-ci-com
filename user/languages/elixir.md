---
title: Building an Elixir Project (beta)
layout: en
permalink: /user/languages/elixir/
---

### Warning

The features described here are still in development and are subject to change without backward compatibility or migration support.

### What This Guide Covers

This guide covers build environment and configuration topics specific to Elixir projects. Please make sure to read our [Getting Started](/user/getting-started/) and [general build configuration](/user/customizing-the-build/) guides first.

## CI Environment for Elixir Projects

To choose the Elixir VM, declare in your `.travis.yml`:

{% highlight yaml %}
language: elixir
{% endhighlight %}

Note that Elixir has requirements regarding the underlying
Erlang OTP Release version.

If the specified OTP Release version (implicity or explicitly)
does not meet this requirement, Travis CI will choose one
for you.

You can also override this OTP Release choice by adding the `otp_release`.
For example:

{% highlight yaml %}
language: elixir
elixir:
  - 1.1.0
otp_release:
  - 18.0
{% endhighlight %}

## Build Matrix

For elixir projects, `env`, `elixir` and `otp_release` can be given as arrays
to construct a build matrix.

## Default commands

By default, the install command is

```shell
mix local.hex --force
mix deps.get
```

and the script command is

```shell
mix test
```

## Environment Variables

The version of Elixir a job is using is available as:

    TRAVIS_ELIXIR_VERSION

As with the Erlang VM, the version of OTP release a job is using is available as:

    TRAVIS_OTP_RELEASE
