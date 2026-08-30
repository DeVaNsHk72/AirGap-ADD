# AirGap-ADD

Simulated acoustic channels for replay-robust, far-field audio deepfake detection.

**Status:** planning. Nothing trained yet.

## The idea

Audio deepfake detectors are benchmarked on clean digital audio. A detector running on
a physical device never receives that. It hears audio that went through a loudspeaker,
a room, and a cheap microphone. Replaying a deepfake through the air launders away the
artifacts detectors look for: published results show one strong detector going from
4.7% to 18.2% EER under replay.

The community's answer so far is to record more real replay data. That does not scale.

This project asks whether the replay channel can be **simulated** well enough that a
detector trained only on simulation generalises to real re-recorded audio.

If it works, replay robustness becomes free.

See [PLAN.md](PLAN.md) for the full research plan, datasets, experiments and timeline.

## Layout

```
src/sim/        acoustic channel simulator (the core contribution)
src/features/   channel-based features: reverb, distortion, spectral tilt
src/models/     small detector + baselines
src/eval/       EER / min-DCF harness
src/deploy/     quantisation and on-device benchmarking
results/        experiment outputs, committed
```

## Setup

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

## Reproducing

Not yet. Scripts land under `scripts/` as each milestone completes.

## Licence

Code MIT. Datasets follow their own licences; ReplayDF, EchoFake, IndicSynth and MLAAD
are non-commercial research releases and are not redistributed here.
