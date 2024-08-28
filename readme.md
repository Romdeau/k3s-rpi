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

## Pihole

Taking an initial stab at this with [this helmchart by MoJo2600](https://github.com/MoJo2600/pihole-kubernetes)

```bash
helm repo add mojo2600 https://mojo2600.github.io/pihole-kubernetes/
helm repo update
helm search repo mojo2600/pihole --versions
```

At time of writing the newest chart is `2.26.1`