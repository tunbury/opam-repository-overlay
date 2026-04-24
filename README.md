# claude-repo

A test opam overlay repository for use with [braid](https://github.com/mtelvers/braid) merge-test.

## Packages

| Package | Description |
|---------|-------------|
| `arrow.dev` | Bindings for Apache Arrow and Parquet |
| `braid.0.1.0` | Build status tracker for opam overlay repositories |
| `braid.dev` | Build status tracker for opam overlay repositories |
| `conf-arrow.1` | Virtual package relying on an Apache Arrow system installation |
| `conf-onnxruntime.1` | Virtual package relying on an ONNX Runtime system installation |
| `dream-encoding.dev` | Encoding primitives for Dream |
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
| `tiff.dev` | Pure OCaml TIFF/GeoTIFF library |
| `wav.dev` | Pure OCaml WAV (RIFF/WAVE) audio file reader and writer |
| `zarr-blosc.0.1.0` | Blosc codec for Zarr - high-performance meta-compressor |
| `zarr-eio.0.1.0` | Eio-based async store implementations for Zarr |
| `zarr-sync.0.1.0` | Synchronous store implementations for Zarr |
| `zarr.0.1.0` | Pure OCaml implementation of Zarr v3 |

## Usage

Test this overlay with braid:

```bash
# Quick dependency check
braid merge-test /path/to/claude-repo --dry-run -o results

# Full build test
braid merge-test /path/to/claude-repo -o results

# Stack with another overlay (claude-repo has higher priority)
braid merge-test /path/to/claude-repo /path/to/other-overlay -o results
```

## Repository Structure

```
claude-repo/
├── repo                              # opam repository metadata
└── packages/
    ├── braid/braid.dev/opam
    ├── imapd/imapd.dev/opam
    └── smtpd/smtpd.dev/opam
```

## Adding as an opam Repository

```bash
opam repository add claude-repo https://github.com/mtelvers/claude-repo.git
```

## License

ISC
