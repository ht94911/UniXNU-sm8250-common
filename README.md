# SM8250 support for UniXNU

This repository supplies shared CPU affinities, GICv3 resources and the 19.2 MHz
architectural timer for Qualcomm SM8250. Device repositories supply RAM and
reserved regions, enabled CPUs, peripheral wiring and board policy.

The DTSI describes eight CPUs, disabled by default. A board enables the required
cores and selects the `ArmCpu` component. The initial resources are derived from
cas hardware descriptions identified in hardware-sources.json. Other SM8250
boards must verify their topology and controller layout.

## Integration

Pin this repository in the device feeds.toml, set board.soc_source to sm8250,
include `dts/sm8250.dtsi`, and add `configs/sm8250.config` and patches/xnu/series to
the ordered lists. From the UniXNU checkout:

```sh
./unixnu defconfig cas_defconfig -D ../UniXNU-cas
./unixnu status --json -D ../UniXNU-cas
./unixnu tree -D ../UniXNU-cas
```

The cas port has device evidence for CPU0 entry, VM and early platform/timebase
initialization. Real timer interrupts, SMP, UFS, GPU and userspace require their
own device results. This source package contains no firmware blobs.

See https://unixnu.com/porting/soc-support and the device porting.toml record.
