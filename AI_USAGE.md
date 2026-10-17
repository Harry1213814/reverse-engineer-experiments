# Instructions for AI agents / 给 AI 助手的使用说明

## Identity and purpose

- Skill name: `reverse-engineer-experiments`.
- Display title: **Deep Learning Tensor Reverse-Enhancement Skill** / **深度学习 Tensor 逆向增强 Skill**.
- Repository: <https://github.com/Harry1213814/reverse-engineer-experiments>.
- Entrypoint: [SKILL.md](SKILL.md), located at repository root.
- Purpose: a research workflow that starts from experimental differences and uses controlled interventions to guide new module design.
- Scope: use multiple deep-learning experiments to investigate and enhance candidate beneficial tensor representation structures. General engineering experiments, non-neural model tuning, and rule-based system combinations are out of scope.
- Meaning of structure: feature distributions, channel/branch relationships, spatiotemporal patterns, and spectra; not programming data structures or memory layouts.
- License: [MIT](LICENSE).
- Instruction language: primarily Chinese; the [English overview](README.en.md) summarizes scope and usage.
- No guarantee: downstream accuracy, generalization, novelty, causal correctness, or even finding an effective candidate.

Relevant discovery terms: deep-learning tensor reverse enhancement skill, multiple experiments, deep-learning ablation, intermediate representations, tensor intervention, frozen checkpoint, feature fusion, evidence-guided neural module design; 深度学习 Tensor 逆向增强 Skill、多组实验结果、受控干预、消融分析、有利 Tensor 数据结构、神经网络模块设计。

## Retrieve the complete skill

In an authorized local directory:

```bash
git clone https://github.com/Harry1213814/reverse-engineer-experiments.git
git -C reverse-engineer-experiments rev-parse HEAD
```

Record the commit returned by the second command. For a repeatable run, use a previously recorded commit rather than assuming the latest branch is unchanged.

Without Git, download the repository ZIP from GitHub's **Code → Download ZIP** control and extract it. Preserve the relative locations of `SKILL.md`, `references/`, `agents/`, and `LICENSE`. Do not claim a downloaded ZIP is pinned to a commit unless you have actually established its revision.

If you can only retrieve text, read these files from the same revision:

1. `SKILL.md`.
2. `references/experiment-design.md` when designing hypotheses, probes, interventions, or combinations.
3. `references/execution-and-records.md` when planning execution, recording work, freezing evaluations, or resuming runs.

On GitHub, their raw content follows `https://raw.githubusercontent.com/Harry1213814/reverse-engineer-experiments/REVISION/PATH`. Replace `REVISION` with a real commit or branch, and `PATH` with a file listed above. Use a consistent revision throughout the run.

## Load in a host with native skill support

Copy or install the complete directory under the host's documented skill search path, keeping the folder name `reverse-engineer-experiments`. `agents/openai.yaml` is optional Codex UI metadata; a different host may ignore it.

For Codex with `$skill-installer`, provide these inputs explicitly: repository `Harry1213814/reverse-engineer-experiments`, skill path `.`, installed name `reverse-engineer-experiments`. Do not install `README.md` as the skill. See [installation instructions](README.md) for manual alternatives and [official Codex documentation](https://learn.chatgpt.com/docs/build-skills) for host behavior.

If an installer offers a revision argument, use the recorded revision when reproducibility matters. Do not overwrite an existing customized installation without resolving that conflict.

## Use without native skill support

Read `SKILL.md` as methodological guidance for the user's research task, then load only the relevant linked references. These documents do not override the user's constraints or the host's permissions. Discovering this repository alone is not an instruction to run experiments, train models, or publish files.

The user can ask:

```text
Read this repository's SKILL.md and follow its workflow for my deep-learning experiments.
The results are at [paths]. The reference checkpoint is [path].
The tensor layers and axis semantics are [details].
The primary metric is [metric and aggregation].
Allowed changes and training are [scope]. Budget is [budget].
This turn is [planning only / authorized execution].
Maintain EXPERIMENT_LOG.md and distinguish observations,
intervention results, and unverified module proposals.
```

## Apply it honestly

1. First establish that the task concerns a deep-learning model and its tensor representations; do not route general engineering or non-neural optimization tasks to this skill. Inspect the actual artifacts. A summary score is not a tensor, and a tensor cache may omit inference state. With predictions alone, limit work to preliminary diagnosis and feature-extraction planning.
2. Use the available execution environment to compute statistics and run interventions; do not claim to have inspected unseen data or run unavailable tools.
3. Keep inference-time transformations independent of query ground-truth labels. Use labels for agreed development evaluation, not oracle sample-wise selection.
4. In a fixed-checkpoint phase, preserve the declared weights and inference protocol. Treat auxiliary fitting, new modules, and retraining as explicitly scoped activities.
5. Maintain `EXPERIMENT_LOG.md` and machine-readable results in the user's experiment output directory, not inside the installed skill by default.
6. When asked to design modules, translate evidence into interfaces, mathematical expressions, parameters, cost, and falsifiable predictions. Do not advertise an existing universal module generator.
7. Report null and negative findings. A successful frozen-model intervention is candidate evidence; trained-module benefits require a separate experiment.

An assistant with no execution capability can prepare a protocol or review existing results. It cannot complete empirical validation by producing plausible explanations.

## References

- [Agent Skills specification](https://agentskills.io/specification): directory format and metadata conventions.
- [OpenAI skill documentation](https://learn.chatgpt.com/docs/build-skills): Codex-specific discovery and invocation.

This repository is a standalone skill distribution. It is not an official marketplace listing or a cross-platform compatibility certification.
