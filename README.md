# SM8250 shared support for UniXNU

Scope: architectural CPU affinities, GICv3 and the19.2MHz timer. Board memory,
reserved ranges, enabled CPUs, panel and peripheral wiring belong in each device.
The initial resources come from the captured Xiaomi10Ultra(cas) hardware facts;
other SM8250 boards must verify their topology and resources. Only cas CPU0 VM/
early-platform/timebase initialization has been observed. Real timer IRQs, SMP,
UFS, GPU and userland are not claimed. This repository supplies no firmware blob.

Device feeds pin this repository commit, set board.soc_source=sm8250, include
sm8250.dtsi, and select configs/sm8250.config plus its patch series. See the
upstreamhttps://unixnu.com/porting/soc-support and device records for evidence.
