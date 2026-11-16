# Changelog

All notable changes to `sailantis/azera-volucer` are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.4.2] - 2026-11-16

First tagged release. Version numbers follow `sailantis/azera-framework`, and
`dev-main` is now aliased to `0.4.x-dev` to match.

### Added

- An HTTP worker that serves Azera requests from persistent volucer workers,
  reusing the framework's `AppContext` container, `Router`, `Dispatcher` and
  middleware pipeline.
