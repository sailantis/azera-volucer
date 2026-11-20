# Changelog

All notable changes to `sailantis/azera-volucer` are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- **The worker delegates routing, 404 and error handling to `Azera\Core\Kernel`.**
  `dispatch()` no longer matches and dispatches inline, so a not-found response, a
  405 with `Allow`, and an exception answered as a 500 all behave exactly as they do
  under FPM or RoadRunner. The application's 404 page is registered once on
  `AppContext` via `Azera\Core\NotFoundHandlerInterface` instead of being threaded
  through the worker.
- **The `$notFoundHandler` constructor argument is now
  `NotFoundHandlerInterface|null`**, not `Closure|null`. It remains only as a test
  override; applications should register the handler on the context.
- **`volucer-worker.php` returns `void`.** Its callable runs once for per-process
  setup and no longer returns a not-found handler. An existing file that returns a
  closure still loads, but the closure is ignored — move the policy onto the context.

## [0.4.2] - 2026-11-16

First tagged release. Version numbers follow `sailantis/azera-framework`, and
`dev-main` is now aliased to `0.4.x-dev` to match.

### Added

- An HTTP worker that serves Azera requests from persistent volucer workers,
  reusing the framework's `AppContext` container, `Router`, `Dispatcher` and
  middleware pipeline.
