# Raspberry Pi K3S Setup

## Flux Setup

I don't even know if FLux supports arm, so here goes nothing

```bash
export GITHUB_TOKEN=<SNIP>
export GITHUB_USER=romdeau

flux bootstrap github \
  --components-extra=image-reflector-controller,image-automation-controller \
  --owner=$GITHUB_USER \
  --repository=k3s-rpi \
  --branch=main \
  --path=./clusters/rpi \
  --read-write-key
```