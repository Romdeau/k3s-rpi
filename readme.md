# Raspberry Pi K3S Setup

## K3s Setup

I need to past this is from my other Doc

## Flux Setup

You should [look at the docs](https://fluxcd.io/flux/installation/), but if you're impatient:

```bash
curl -s https://fluxcd.io/install.sh | sudo bash
```

Flux does work on arm, my install uses about 400mb of RAM, which is relatively heavy, but not too bad for what we get here.

```bash
export GITHUB_TOKEN=<SNIP>
export GITHUB_USER=romdeau
export GITHUB_FLUX_REPO=k3s-rpi

flux bootstrap github \
  --components-extra=image-reflector-controller,image-automation-controller \
  --owner=$GITHUB_USER \
  --repository=$GITHUB_FLUX_REPO \
  --branch=main \
  --path=./clusters/rpi \
  --read-write-key
```