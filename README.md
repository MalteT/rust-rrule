<h1 align="center">RRule.rs</h1>
<p align="center">A pure and efficient Rust implementation of recurrence rules as defined in the iCalendar RFC..</p>
<p align="center">
  <a href="https://travis-ci.com/fmeringdal/rust_rrule"><img src="https://travis-ci.com/fmeringdal/rust_rrule.svg?branch=main" /></a>
  <a href="https://codecov.io/gh/fmeringdal/rust_rrule"><img src="https://codecov.io/gh/fmeringdal/rust_rrule/branch/main/graph/badge.svg" /></a>
  <a href="https://crates.io/crates/rrule"><img src="https://img.shields.io/crates/v/rrule.svg" /></a>
</p>

## Warning

This crate is not production ready yet. Dates and recurrence rules are quite complicated and
takes time to get right. Even though this crate is well tested (high code coverage), there are still
tests missing regarding edge cases in stuff like DST, time zone and rfc_string parsing (contributions are very
welcome!).
Use at your own risk!

## Library Usage

```rust
use rrule::RRule;

// RRule that starts 2012.02.01 and occurs daily for 3 days.
let rrule: RRule = "DTSTART:20120201T093000Z\nRRULE:FREQ=DAILY;COUNT=3".parse().unwrap();

// Get all recurrences of the rrule
let recurrences = rrule.all(); // Or rrule.into_iter().collect::<Vec<_>>(); if you want to leverage iterators
assert_eq!(recurrences.len(), 3);
```

See more examples at [docs.rs](https://docs.rs/rrule)


## Command Line Tool Usage
Install the command line tool with:
```
$ cargo install rrule
```

Then run it with:
```
$ rrule "DTSTART:20120201T093000Z\nRRULE:FREQ=DAILY;COUNT=3"
```

## License

This project is licensed under the [MIT license].

[mit license]: https://github.com/fmeringdal/rust_rrule/blob/main/LICENSE

## Inspired by

- [python-dateutil library](http://labix.org/python-dateutil/)
- [rrule.js](https://github.com/jakubroztocil/rrule)

## TODOS

- cache
- more tests around string parsing and validation
