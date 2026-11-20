# embodiment-card

**Robot embodiment card validator and renderer.** Part of [Robotics Studio](https://auraone.ai/open/robotics-studio).

```bash
python -m pip install "embodiment-card==0.1.2"
embodiment-card validate examples/mock_so101_card.json
```

From a source checkout this prints `valid`.

`embodiment-card` validates and renders structured robot embodiment metadata for
dataset and vision-language-action release review.

## At a Glance

| | |
| --- | --- |
| Job | Make robot hardware, sensing, action, frame, control, environment, and limitation assumptions reviewable. |
| Built for | Robotics dataset curators, VLA researchers, release reviewers, and documentation owners. |
| Differentiator | Dependency-free schema validation plus Markdown and Hugging Face README rendering. |
| Produces | A validated JSON card or a human-readable embodiment card for release documentation. |

## Install

```bash
python -m pip install "embodiment-card==0.1.2"
```

## Verified Quickstart

Run from a source checkout:

```bash
embodiment-card validate examples/mock_so101_card.json

embodiment-card render examples/mock_so101_card.json \
  --hf-readme \
  --out /tmp/SO101-EMBODIMENT.md
```

The bundled SO-101 fixture validates and renders Hugging Face-compatible YAML
tags followed by an embodiment card.

## Required Disclosure

The v1 card requires:

- name and robot morphology;
- at least one sensor;
- action-space metadata;
- at least one coordinate frame;
- positive control rate;
- teleoperation method;
- environment assumptions;
- safety boundaries and known limitations.

Validation checks required fields and a small set of structural constraints. It
does not verify hardware, calibration, units, coordinate transforms, or the
truth of a disclosure.

## Runtime, Data, and Network Boundary

- The CLI reads one local JSON file and writes Markdown to a file or stdout.
- It does not inspect robot media, connect to hardware, contact Hugging Face, or
  make network requests.
- `--hf-readme` formats local text only; it does not create or update a Hub
  repository.
- No redaction is applied. Review cards for private paths, operators, sites, or
  hardware identifiers before sharing them.

## Limitations

- Validation covers required fields and simple structure only. It does not check
  calibration, coordinate transforms, units, or hardware truth.
- Rendered cards remain self-reported documentation, not a safety review,
  hardware certification, or deployment approval.

## Compatibility

`robostudio-engine` exposes a direct `robostudio card` integration that imports
`embodiment-card` when the package is installed or available in the AuraOne
monorepo. The standalone card format can also be embedded in any dataset or
model README.

## Publication Status

Verified on 2026-07-13:

- PyPI: [`embodiment-card==0.1.2`](https://pypi.org/project/embodiment-card/0.1.2/)
- GitHub release: [`v0.1.2`](https://github.com/auraoneai/embodiment-card/releases/tag/v0.1.2)
- Bundled cards describe mock tutorial datasets and do not establish hardware
  validation or safety assurance.

## Next Action

Fill a card from one real dataset's reviewed metadata, have the hardware owner
verify frames and control rate, then publish the rendered disclosure beside the
dataset.

Part of the AuraOne robotics dataset QA workflow:
[lerobot-quality-gates](https://auraone.ai/open/lerobot-quality-gates) →
[Robotics Studio](https://auraone.ai/open/robotics-studio).

---

Need reviewed demonstration data or dataset quality operations at scale?
[Talk to AuraOne](https://auraone.ai/contact?from=open:embodiment-card)
