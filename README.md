# Luminos

An AI model built from scratch, mainly focused on preventing catastrophic
forgetting — a learning project in model architecture and training.

Catastrophic forgetting is the classic failure mode of neural networks:
train on task/domain B after task/domain A, and performance on A collapses,
because gradient updates for B overwrite the weights that encoded A. Luminos
is an exploration of architectures and training regimes that push back
against this, built from first principles rather than by fine-tuning an
existing model.

## What it's exploring

This is a learning project, so the point isn't just "does it work" but
understanding *why* each technique helps. Areas Luminos is built around:

- **Elastic Weight Consolidation (EWC)-style regularization** — penalizing
  changes to weights that were important for previously learned tasks,
  estimated via a Fisher information approximation.
- **Experience replay / rehearsal buffers** — interleaving a sample of old
  task data with new task data during training so old representations keep
  getting reinforced instead of purely overwritten.
- **Modular / mixture-of-experts style routing** — isolating task-specific
  computation into separate expert sub-networks with a gating mechanism, so
  new learning can route around (rather than through) weights critical to
  old tasks.
- **Progressive network growth** — adding new capacity (columns/layers) for
  new tasks while freezing weights tied to earlier ones, with lateral
  connections so new tasks can still draw on old representations.
- **Custom training loop and evaluation harness** — built from scratch (not
  a wrapper around an existing framework's continual-learning module) so the
  tradeoffs between these approaches are actually visible and measurable,
  not just cited from a paper.

## Status

🚧 **Early / active development.** I'm currently working on this — architecture
and training code are both still evolving, and there's no trained checkpoint
or benchmark results yet. This repo will fill in as the implementation and
experiments progress.

## License

MIT — see [LICENSE](LICENSE).