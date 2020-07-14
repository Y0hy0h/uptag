# uptag: Update tags in Dockerfiles.
[![CI status](https://github.com/Y0hy0h/uptag/workflows/CI/badge.svg)](https://github.com/Y0hy0h/uptag/actions?query=workflow%3ACI) [![Licensed under MIT or Apache-2.0](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue)](#license)

Tired of manually looking up whether the base images you depend on have been updated?

```
$ uptag check ./Dockerfile
Report for Dockerfile at `/home/y0hy0h/Dockerfile`:

1 breaking update(s):
ubuntu:18.03
   -!> 20.10

1 compatible update(s):
ubuntu:18.03
    -> 18.04
```

`/home/y0hy0h/Dockerfile`:
```Dockerfile
# uptag --pattern "<!>.<>"
FROM ubuntu:18.03
```

## Pattern syntax
Use `<>` to match a number. Everything else will be matched literally.
- `<>.<>.<>` will match `2.13.3` but not `2.13.3a`.
- `debian-<>-beta` will match `debian-10-beta` but not `debian-10`.

Specify which numbers indicate breaking changes using `<!>`. Uptag will report breaking changes separately from compatible changes.
- Given pattern `<!>.<>.<>` and the current tag `1.4.12`
  - compatible updates: `1.6.12` and `1.4.13`
  - breaking updates: `2.4.12` and `3.5.13`

## License
Licensed under either of

 * Apache License, Version 2.0
   ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license
   ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution
Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.