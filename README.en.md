# Deep Learning Tensor Reverse-Enhancement Skill: Finding Better Tensor Structures from Multiple Experiments

**A research workflow that starts from experimental differences and uses controlled interventions to guide new module design.**

[中文说明](README.md) · [Skill instructions](SKILL.md) · [Instructions for AI agents](AI_USAGE.md) · [MIT license](LICENSE)

This is an instruction-based skill specifically for **deep-learning models**, used by AI coding and research assistants. It compares multiple training or ablation experiments, turns differences in intermediate tensors into testable hypotheses, and uses interventions on an existing checkpoint to inform feature enhancement, fusion, or new neural modules. It is not a general-purpose workflow for all engineering experiments or non-neural system optimization.

Here, "tensor structures" means representation statistics and relationships, such as distributions, channel or branch relationships, spatiotemporal patterns, and spectra. It does not mean programming data structures or memory layouts. "Beneficial" is a hypothesis to investigate, not a promised outcome. The technical invocation name remains `reverse-engineer-experiments`.

**It does not guarantee an improvement in downstream accuracy or any other metric.** It does not guarantee a useful intervention, a correct causal explanation, or a novel module. A successful intervention on frozen weights does not establish that a proposed module will improve results after training from scratch.

## Background

The idea was inspired by reverse engineering. In my own machine-learning optimization work, I usually followed a cycle: read papers, discover a module, assess whether it might help, integrate it into my model, train, and judge the results.

Much of the time went into trying different modules. Before running an experiment, I often did not know whether a module suited my task, data, or current model. Its success in another paper did not tell me which problem it would solve in my system.

I wanted to investigate the problem from the tensor side. Could an AI assistant use analysis code to compare intermediate representations from better and worse experiments? What distributions, relationships, or local structures might matter? What operation might strengthen a potentially useful structure?

An explanation alone would not be enough. The assistant should modify a tensor according to its hypothesis, feed that tensor back through the original model with the original checkpoint weights, and measure the result. This provides an opportunity to test a proposed change before training a new module.

My initial intuition was: if accuracy improves, perhaps we have found a useful structure. This workflow treats that result as candidate evidence requiring controls and confirmation, rather than proof of a unique cause. Scale changes, normalization, parameter selection, or adaptation to one particular checkpoint may offer alternative explanations.

If the evidence supports further work, the operation can inform a mathematical transformation or module design, followed by training from scratch and ablation studies. Whether this reduces trial-and-error costs or improves the eventual model remains an empirical question for each task.

## What the workflow does

1. Align samples, data splits, preprocessing, inference state, checkpoints, and metric definitions; reproduce the baseline.
2. Compare predictions and relevant tensor properties, optionally using carefully controlled probes.
3. Translate hypotheses into selective destruction, enhancement, identity, and matched-control interventions within a fixed model.
4. Search within a declared development budget. Test combinations against their strongest individual component.
5. Freeze configurations before confirmation, retain failures, and keep a persistent experiment log.
6. Translate evidence into module hypotheses; implement and train them only within the user's declared next-stage scope.

Tensor analysis normally means that an assistant writes and runs analysis scripts, then inspects their artifacts. It does not require pasting every tensor value into a conversation.

## Scope and limitations

The workflow is suited to comparing deep-learning experiments and ablations, inspecting intermediate tensors, and testing feature interventions in multi-branch, multiscale, temporal, or other neural architectures. Classification, regression, and neural retrieval are in scope when the subject is a deep model's tensor representations. If only predictions from a deep model are available, start with preliminary diagnosis and a feature-extraction plan; do not claim tensor reverse enhancement has been completed.

General engineering trials, traditional non-neural model tuning, rule-based ranking, and arbitrary score-combination tasks are out of scope. Having multiple experimental scores alone does not make this skill applicable.

Aggregate scores alone are insufficient for tensor-level validation. Independent models need not assign the same meaning to matching channel indices. Previously reused test data cannot be relabeled as an untouched holdout. A chat-only assistant can help plan or review work, but cannot claim it ran an experiment.

The current repository contains a research workflow, not a universal tensor analyzer, ready-made neural-module library, automatic architecture search system, or training platform. Its operator examples are not an exhaustive whitelist. A capable assistant can write project-specific code, but an end-to-end general module generator has not been validated here.

Moving from an intervention to a module requires a new specification of interfaces, dimensions, parameterization, initialization, normalization, and cost. Retrained modules need their own baselines and ablations. A failed intervention on one frozen checkpoint also does not rule out a structure's value after retraining.

## Install

In a Codex environment with the built-in installer, use:

```text
Use $skill-installer to install the skill from
https://github.com/Harry1213814/reverse-engineer-experiments.
The skill is at repository root (path: .).
Use the installed name reverse-engineer-experiments.
```

Alternatively, clone the repository into a skill location recognized by your host. For the user-level directory in current Codex documentation:

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/Harry1213814/reverse-engineer-experiments.git "$HOME/.agents/skills/reverse-engineer-experiments"
```

For Windows PowerShell and environment-specific installer paths, see the [Chinese installation instructions](README.md). Choose one installation method and inspect an existing installation before replacing it. Some bundled installers use `$CODEX_HOME/skills` or `~/.codex/skills`; follow your environment's installer documentation. See [OpenAI's official skill documentation](https://learn.chatgpt.com/docs/build-skills) for current discovery and invocation behavior.

## Use

```text
Use $reverse-engineer-experiments.

Multiple deep-learning experiments and results: [paths and differences].
Reference model, checkpoint, data and inference entry point: [paths].
Tensor layers, axis semantics and structures to investigate: [details].
Question and primary metric: [including aggregation and success criteria].
Allowed intervention points: [layers, tensors or combination rules].
Training/calibration permissions: [specific scope].
Development/confirmation splits and prior exposure: [details].
Budget and output directory: [details].

First audit the available evidence and resolve material unknowns.
Keep EXPERIMENT_LOG.md with purposes, configurations, outcomes, controls,
and next steps. Separate measured gains, mechanism hypotheses,
and module designs requiring retraining.
```

Specify whether the task is planning only or authorized execution. To move on to module implementation or retraining, explicitly provide the allowed changes, training protocol, compute budget, and evaluation data. The repository does not supply a task's model or training code.

## For other AI agents

Read [AI_USAGE.md](AI_USAGE.md), then [SKILL.md](SKILL.md) and its relevant references. Agents without native skill support can use these Markdown files as task-level methodological guidance. Keep the directory structure and record the commit used. A public repository is retrievable; publication does not guarantee indexing by any search engine or AI platform.

The skill instructions and references are primarily in Chinese; an assistant must be able to read them. Native loading and metadata support vary by host, so this is not a claim of universal client compatibility.

## Expected artifacts and validation status

Typical outputs include a research agreement, reproducible baseline, candidate and failure records, intervention/control results, a frozen confirmation record, `EXPERIMENT_LOG.md`, and evidence-linked mathematical or module proposals.

The skill has received structural checks and an assistant application check for frozen-checkpoint feature intervention. These concern workflow interpretation, **not downstream performance benchmarks**. An earlier version also received a retrieval-system combination scenario check; that check does not establish the current skill's applicability to general retrieval engineering or other non-deep-learning experiments. No private experiment data, model weights, or cross-task accuracy benchmark are included.

No useful candidates, negative effects, and unresolved explanations are valid outcomes and must be reported. The project makes no claim that following the workflow will improve accuracy, generalization, efficiency, or scientific novelty.

## License

[MIT](LICENSE). Preserve the required copyright and permission notices. The license's warranty disclaimer applies; research conclusions and downstream gains are not guaranteed.
