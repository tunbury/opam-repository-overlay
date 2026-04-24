# opam-repository-overlay

An opam overlay providing packages that are not (yet) in the main
[opam-repository](https://github.com/ocaml/opam-repository), continuously
tested against the upstream repository via GitHub Actions.

## Continuous build testing

Every push, pull request, and merge-queue entry triggers a full build of every
package in this overlay on self-hosted runners, using
[`day10`](https://github.com/mtelvers/day10) for cached, containerised opam
dependency resolution.

- **Solve, then build.** Packages are first filtered by dependency solvability
  (`day10 health-check --dry-run`), then the solvable set is built for real.
- **Regression gate.** Each run is compared against the previous successful run
  on `main`. A package that went from `success` to any failure state blocks
  the merge queue, so broken changes cannot land.
- **Rich step summaries.** Every run publishes success/failure counts, the
  tail of each failing build log, and a diff against the previous run (newly
  broken, newly fixed, newly added, removed).

See [`.github/workflows/ci.yml`](.github/workflows/ci.yml) for the full pipeline.

## Using as an opam overlay

Add this repository as a higher-priority overlay on top of your existing opam
repositories:

```bash
opam repository add tunbury-overlay https://github.com/tunbury/opam-repository-overlay.git
opam update
```

Packages in this overlay take precedence over those in
`ocaml/opam-repository`. To remove it:

```bash
opam repository remove tunbury-overlay
```

## Packages

| Package | Description |
|---------|-------------|
| `arrow.dev` | Bindings for Apache Arrow and Parquet |
| `braid.0.1.0` | Build status tracker for opam overlay repositories |
| `braid.dev` | Build status tracker for opam overlay repositories |
| `conf-arrow.1` | Virtual package relying on an Apache Arrow system installation |
| `conf-blosc.1` | Virtual package relying on a Blosc system installation |
| `conf-gdal.1` | Virtual package relying on a GDAL system installation |
| `conf-onnxruntime.1` | Virtual package relying on an ONNX Runtime system installation |
| `day10-tui.dev` | Terminal UI for browsing CI build results from GitHub Actions |
| `dream-encoding.dev` | Encoding primitives for Dream |
| `embeddings-size.0.1.0` | Calculate total size of Tessera embeddings for a geographic region |
| `gdal.0.1.0` | OCaml bindings to GDAL's raster C API |
| `hilite.dev` | Build time syntax highlighting |
| `imapd.dev` | IMAP4rev2 server implemented in OCaml with EIO |
| `jpeg.dev` | Pure OCaml JPEG library |
| `mp3.dev` | Pure OCaml MPEG-1/2/2.5 Audio Layer I/II/III encoder and decoder |
| `npy.dev` | Read and write NumPy .npy files |
| `ocaml-slurm.dev` | OCaml client library for Slurm REST API |
| `octopus_energy.dev` | OCaml library and CLI for Octopus Energy API |
| `onnxruntime.0.1.0` | OCaml bindings to ONNX Runtime via C shim |
| `onnxruntime.dev` | OCaml bindings to ONNX Runtime via C shim |
| `opam-hub.0.1.0` | Gated opam overlay repository server |
| `png.dev` | Pure OCaml PNG library |
| `prometheus-app.dev` | Report metrics for Prometheus using Cohttp and Eio |
| `prometheus.dev` | Client library for Prometheus monitoring |
| `repo_tool.dev` | Generate opam repository from git repositories |
| `smtpd.dev` | An SMTP server implemented in OCaml |
| `solver-service-api.dev` | Cap'n Proto API for the solver service |
| `solver-service.dev` | Choose package versions to test |
| `solver-worker.dev` | OCluster worker that can solve opam constraints |
| `stac_client.dev` | OCaml STAC API client with Planetary Computer signing |
| `stac_server.dev` | GeoTessera STAC API server and sync tool |
| `tailwindcss.dev` | TailwindCSS prebuild command line on opam |
| `tessera-dpixel.dev` | Tessera dpixel tool in OCaml |
| `tessera-pipeline.dev` | Tessera Pipeline in OCaml |
| `tiff.dev` | Pure OCaml TIFF/GeoTIFF library |
| `wav.dev` | Pure OCaml WAV (RIFF/WAVE) audio file reader and writer |
| `zarr-blosc.0.1.0` | Blosc codec for Zarr - high-performance meta-compressor |
| `zarr-eio.0.1.0` | Eio-based async store implementations for Zarr |
| `zarr-sync.0.1.0` | Synchronous store implementations for Zarr |
| `zarr.0.1.0` | Pure OCaml implementation of Zarr v3 |

## Repository Structure

```
opam-repository-overlay/
├── repo                              # opam repository metadata
├── packages/                         # one subdirectory per package
│   └── <package>/<package>.<version>/opam
└── .github/workflows/ci.yml          # regression-gated build matrix
```

## License

ISC
