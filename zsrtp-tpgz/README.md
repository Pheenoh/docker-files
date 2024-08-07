# TPGZ Docker Images

These images are used for running [TPGZ](https://github.com/zsrtp/tpgz)'s tests against various versions of Twilight Princess.

To have these build, you will need each respective version of Twilight Princess in each folder, renamed to their corresponding game code.

# Pushing up images the ghcr.io

1. Set PAT token

```bash
export GHCR_TOKEN=<pat_token>
```

2. Add images to each individual folder, (ex: GCN_NTSCU/GZ2E01.iso, GCN_PAL/GZ2P01.iso, etc.)

3. Run make

```bash
make
```