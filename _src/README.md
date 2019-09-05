std/lib: for php
====

## Overview

`std/lib` is a *very* ambitious project.  

`std/lib` is a set of libraries, meant to primarily be implemented in PHP to solve many problems of general PHP development and within the PHP ecosystem.  

**`std/lib` is not a framework**.  It is a set of common APIs to solve common problems faced by PHP developers in a vendor-neutral, *framework-neutral* way.  

**`std/lib` SHALL NOT CREATE IMPLEMENTATIONS OF FUNTIONALITY ITSELF, UNLESS ABSOLUTELY REQUIRED TO DO SO.**

Priorities to implementation of wrappers will be where PHP suffers the most: Process Control, Threading, Asynchronous Execution, Error Handling, and functionality you would expect to find in a “standard runtime library”.

## Goals

Instead of re-implementing things that already exist, `std/lib` is here to:

 - Provide wrappers around standard PHP functionality, well-known, and lesser-known libraries/frameworks/functionality:

   <small>These may be fairly transparent wrappers (`Std\Redis\Client` is basically the same as predis, just with an adapter interface to use a different implementation)</small>

   <small>These may be as more complex anti-corruption layers which improve/hide poorly exposed but well implemented libraries.</small>

   <small>These may be facades, which simplify complex operations.</small>

 - Provide bridges in/out of various existing frameworks.
   
   <small>While this is improving with PSR-x standards, it's still a big giant mess if you want to use more than one framework, parts from different frameworks, parts from framework-independent libraries, or any mix of the three.</small>
   
 - Help standardize things
   
   <small>The hope here is that by supporting many library implementations with quality APIs, as well as quality wrappers around base functionality that it will become a de-facto standard of how to access _X_.</small>

Again, primitive functionality aside (string/array type low-level functionality -- or "glue" for cross-library/framework libraries) this is **NOT** an attempt to re-implement any _functionality_.  

## Guarantees

The purpose is _only_ to provide existing implementations wrapped in a *type-safe* and *<u>strict</u>* API.  Additionally, unless **clearly** specified otherwise, stable releases MUST provide the following objective guarantees:

 - Generally, independent of php extensions installed.  See [Extensions](Extensions.md)
 -  No PHP-level `E_*` notices, warnings, or errors.  Only exceptions are thrown in error situations.
 - No "mixed" return types or parameters - except in those that are for the normalization or determination of values and types, or for development.
 - No globally namespaced functions or classes.

_This list is expected to expand._

We also hope to provide the following subjective guarantees:

 - A stable, well thought-out exception tree.
 - The best "backend" implementation by default.  Zend, Symfony, Laravel, League, Cake, Concrete, or "other" framework-independent implementation -- we have no bias, only bias twoards well-written code.
 - Through various bridges, providing all frameworks with implementations of "mission critical" quality code.

## Wrappers

Standard library implementations will, in order of preference:

- Compose new classes (composition) with underlying implementations passed-in with dependency injection, with the “preferred” implementation auto-injected. (alternatively, create internally if absolutely necessary)
- Inherit underlying implementations where it must be done, i.e, adapters.  Multiple adapters that inherit different implementations MAY be provided as separate packages (i.e, adapter for Zend, adapter for Symfony, etc).
- Fork project(s) and provide slightly modified versions of packages, keeping it up-to-date with the upstream version where absolutely necessary.
- Implement it ourselves, as a final resort.

## Planned Namespace Use

Example:

- `std\` namespace for generics.
- `stdlib\` namesapce for implementations.
- `std\NetUtil` for basic utilities.
- `stdlib\Net\Server` for full implementations.



## Next Steps

**ALL CODE IS SUBJECT TO CHANGE AT PRESENT**.  Currently, `std/lib` is in *very* early stages of development. Until the 1.0 release, anything is subject to change.

 - [ ] Which libraries are most important from the [Library Wish List](Library-Wish-List.md)? - Put into a fully prioritized list.
 - [ ] What is the best way to organize the base array, string, and low-level utility functionality?
 - [ ] Are there other guarantees we should consider?
 - [ ] Begin implementation
    - [ ] Implement “base” library - strings, array, value validation, and other core functions.
    - [ ] Implement `app-*` libaries.
    - [ ] (Expand out to top 3 priorities in Wish List)
 - [ ] Are there other well known frameworks we should consider full or partial compatibility with?
 - [ ] What is the minimum quality that will be acceptable for stable releases?
 - [ ] What is the minimum quality that will be acceptable for development releases?
 - [ ] Get public feedback
 - [ ] Get public interest
 - [ ] Does BSD vs MIT licensing really matter?
 - [ ] Why is Rust, for example, licensed under Apache 2 as well as BSD (or MIT?)

