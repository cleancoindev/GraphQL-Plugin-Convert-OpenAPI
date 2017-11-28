# NAME

GraphQL::Plugin::Convert::OpenAPI - convert OpenAPI schema to GraphQL schema

# PROJECT STATUS

| OS      |  Build status |
|:-------:|--------------:|
| Linux   | [![Build Status](https://travis-ci.org/graphql-perl/GraphQL-Plugin-Convert-OpenAPI.svg?branch=master)](https://travis-ci.org/graphql-perl/GraphQL-Plugin-Convert-OpenAPI) |

[![CPAN version](https://badge.fury.io/pl/GraphQL-Plugin-Convert-OpenAPI.svg)](https://metacpan.org/pod/GraphQL::Plugin::Convert::OpenAPI)

# SYNOPSIS

    use GraphQL::Plugin::Convert::OpenAPI;
    use Schema;
    my $converted = GraphQL::Plugin::Convert::OpenAPI->to_graphql(
      sub { Schema->connect }
    );
    print $converted->{schema}->to_doc;

# DESCRIPTION

This module implements the [GraphQL::Plugin::Convert](https://metacpan.org/pod/GraphQL::Plugin::Convert) API to convert
a [JSON::Validator::OpenAPI](https://metacpan.org/pod/JSON::Validator::OpenAPI) specification to [GraphQL::Schema](https://metacpan.org/pod/GraphQL::Schema) etc.

It uses, from the given API spec:

- the given "definitions" as output types
- the given "definitions" as input types when required for an
input parameter
- the given operations as fields of either `Query` if a `GET`,
or `Mutation` otherwise

The queries will be run against the spec's server.

# ARGUMENTS

To the `to_graphql` method: a URL to a specification, or a filename
containing a JSON specification, of an OpenAPI v2.

# PACKAGE FUNCTIONS

## field\_resolver

This is available as `\&GraphQL::Plugin::Convert::OpenAPI::field_resolver`
in case it is wanted for use outside of the "bundle" of the `to_graphql`
method.

# DEBUGGING

To debug, set environment variable `GRAPHQL_DEBUG` to a true value.

# AUTHOR

Ed J, `<etj at cpan.org>`

Parts based on [https://github.com/yarax/swagger-to-graphql](https://github.com/yarax/swagger-to-graphql)

# LICENSE

Copyright (C) Ed J

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.
