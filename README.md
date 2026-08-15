<h1 align="center">
  <strong>Robotics Research Corpus</strong>
</h1>
<h3 align="center">Data-driven, auto-validated literature review for robotics research</h3>

<div align="center">

[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/tobias-weiss-ai-xr/robotics-research/validate.yml?label=CI&logo=github)](https://github.com/tobias-weiss-ai-xr/robotics-research/actions/workflows/validate.yml)
[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-brightgreen.svg?logo=github)](https://tobias-weiss-ai-xr.github.io/robotics-research/)

</div>

> 🤖 **Robotics research corpus:** manipulation, locomotion, perception, planning,
> learning, human-robot interaction, multi-robot systems, simulation, and surveys —
> analyzed with the same taxonomy → momentum → burst → gap pipeline as
> [graph-research](https://github.com/tobias-weiss-ai-xr/graph-research) and
> [ai-literacy-research](https://github.com/tobias-weiss-ai-xr/ai-literacy-research).

## What you get

| Capability | How |
|------------|-----|
| 📄 **Curated corpus** | `papers.yaml` is the source of truth — one structured entry per paper |
| ✅ **Auto-validation** | `scripts/validate_papers.py` checks schema, duplicates, URL normalization, LaTeX artifacts |
| 🧾 **Auto-generated README** | `scripts/generate_readme.py` renders the paper list grouped by your taxonomy |
| 📊 **Statistics & trends** | `scripts/standard_stats.py` → `statistics.json` (momentum, gaps, bursts, venues, authors) |
| 🔍 **Literature review report** | `scripts/analysis/generate_reports.py` → `docs/research/literature_review.md` + `trends.md` |
| 🧭 **Topic planning** | `tools/topic_planner.py`, `tools/trend_scanner.py`, `tools/landscape_analyzer.py`, `tools/brief_generator.py` |
| 🔎 **New paper discovery** | `scripts/fetch/fetch_new_papers.py` (arXiv), `fetch_other_sources.py` (dblp/crossref/europepmc), `fetch_openalex_bulk.py` |
| 🐙 **GitHub repos discovery** | `scripts/fetch/fetch_github_repos.py` (optional, config-driven via `github_queries` in taxonomy.yaml) |
| 🦊 **GitLab projects discovery** | `scripts/fetch/fetch_gitlab_repos.py` (optional, config-driven via `gitlab_queries` in taxonomy.yaml) |
| 🏠 **Codeberg repos discovery** | `scripts/fetch/fetch_codeberg_repos.py` (optional, config-driven via `codeberg_queries` in taxonomy.yaml) |
| 🖥️ **GitHub Pages site** | `docs/index.html` — searchable, filterable paper browser |
| 🤖 **Agentic workflow** | `AGENTS.md` + `config/taxonomy.yaml` make this repo agent-friendly by design |

## 🚀 Quick Start

```bash
# Validate + generate all outputs
python3 scripts/validate_papers.py && python3 scripts/generate_readme.py && python3 scripts/standard_stats.py && python3 scripts/analysis/generate_reports.py

# Discover new papers from arXiv
python3 scripts/fetch/fetch_new_papers.py --months 12 --dry-run   # preview
python3 scripts/fetch/fetch_new_papers.py --local                 # append to papers.yaml

# Explore the corpus
python3 tools/trend_scanner.py --months 12
python3 tools/landscape_analyzer.py
python3 tools/topic_planner.py --top 10
```

## 📖 How it works

```
config/taxonomy.yaml ──► papers.yaml ──► validate_papers.py
                          │   ▲              │
                          ▼   └── fetch_* ───┘
                   generate_readme.py ──► README.md (auto)
                          │
                          ▼
                  standard_stats.py ──► statistics.json, docs/papers.json
                          │
                          ▼
              analysis/generate_reports.py ──► docs/research/*.md
```

- **Never edit README.md directly** — it is generated from `papers.yaml`.
- The **taxonomy lives in one place** (`config/taxonomy.yaml`); every script reads it via `scripts/research_config.py`.
- **CI (validate.yml)** runs on every push/PR and weekly to discover new papers.

## 🧪 Local pipeline (all in one)

```bash
# Full pipeline (validate → README → stats → reports)
python3 scripts/validate_papers.py && python3 scripts/generate_readme.py && python3 scripts/standard_stats.py && python3 scripts/analysis/generate_reports.py
```

## 🤖 Agentic workflow (AGENTS.md)

This repo is designed to be driven by coding agents (OpenCode, Claude Code, …):

- **Spec-style guardrails** in `AGENTS.md` — agents know the pipeline, never edit README, always re-validate.
- **One config file** to change → one re-run to verify (low context cost for agents).
- **Auto-validation** gives agents an objective pass/fail signal.
- **Weekly discovery** keeps the corpus fresh without human babysitting.

## 📚 Paper list

- [📚 Manipulation & Grasping](#manipulation-&-grasping)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Application](#application)
  - [Development](#development)
  - [Systems & Technology](#systems-&-technology)
- [📚 Locomotion & Mobility](#locomotion-&-mobility)
  - [Theory](#theory)
  - [Method](#method)
  - [Application](#application)
  - [Development](#development)
- [📚 Perception & Sensing](#perception-&-sensing)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Application](#application)
  - [Development](#development)
  - [Systems & Technology](#systems-&-technology)
  - [Evaluation & Benchmarks](#evaluation-&-benchmarks)
- [📚 Planning & Control](#planning-&-control)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Development](#development)
- [📚 Learning & Adaptation](#learning-&-adaptation)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
- [📚 Human-Robot Interaction](#human-robot-interaction)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Application](#application)
- [📚 Multi-Robot Systems](#multi-robot-systems)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Development](#development)
  - [Systems & Technology](#systems-&-technology)
- [📚 Simulation & World Models](#simulation-&-world-models)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Application](#application)
  - [Development](#development)
  - [Systems & Technology](#systems-&-technology)
  - [Evaluation & Benchmarks](#evaluation-&-benchmarks)
- [📚 Surveys & Taxonomies](#surveys-&-taxonomies)
  - [Theory](#theory)
  - [Mechanism](#mechanism)
  - [Method](#method)
  - [Application](#application)
  - [Evaluation & Benchmarks](#evaluation-&-benchmarks)
  - [Reviews & Surveys](#reviews-&-surveys)

### Manipulation & Grasping

#### Theory

##### 2026

- [2026] **DCIRNet: Depth completion with iterative refinement for dexterous grasping of transparent and reflective objects** *Neurocomputing* [[paper](https://arxiv.org/abs/2506.09491)]
- [2026] **Aligning robotic manipulation with human cognitive modalities: studies in perception, language, imitation, and foresight** *University of Edinburgh* [[paper](https://doi.org/10.7488/era/7586)]
- [2026] **A Bio‐Functional Mimetic Robot for Versatile Tasks From Cross‐Scale Manipulation to Limb‐Tool Integration** *Advanced Science* [[paper](https://doi.org/10.1002/advs.76527)]
- [2026] **Mechanical Design Strategies of Dexterous Robotic Hands for Enhanced Precision Grasping: A Review** *Robotics* [[paper](https://doi.org/10.3390/robotics15080146)]
- [2026] **Underwater Grippers for Dexterous Manipulation: A Review on Design and Enabling Technologies** *Journal of Field Robotics* [[paper](https://doi.org/10.1002/rob.70277)]
- [2026] **When Contact Becomes Support: Auditing and Repairing Contact-Topology Failures in Programmatic Dexterous Grasp Search** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20922500)]
- [2026] **Functional grasping of floating tools in zero-gravity space using reinforcement learning for dexterous robotic hands** *Science China Technological Sciences* [[paper](https://doi.org/10.1007/s11431-026-3327-y)]
- [2026] **Towards Advanced Intelligent and Perceptive Soft Grippers** *Advanced Intelligent Systems* [[paper](https://doi.org/10.1002/aisy.202501459)]
- [2026] **A Tactile-Driven Hierarchical Reinforcement Learning Framework for Dexterous Robotic Manipulation** *Informatica* [[paper](https://doi.org/10.31449/inf.v50i11.13667)]
- [2026] **Utilizing Spatially Varying Fiber Arrays in Soft Morphing Surfaces for Grasping Applications** *Journal of Mechanisms and Robotics* [[paper](https://doi.org/10.1115/1.4071597)]
- [2026] **Distributed and stretchable tactile sensing for dexterous robotic hands based on a crosslinked interpenetrating network** *Science China Materials* [[paper](https://doi.org/10.1007/s40843-025-3840-3)]
- [2026] **Miniaturized 3D Magnetic Force Sensor via Laser‐Assisted Folding and Magnetization for Enhanced Robotic Dexterity** *Advanced Science* [[paper](https://doi.org/10.1002/advs.202524321)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **Design and evaluation of a tendon-and-linkage hybrid-driven humanoid dexterous hand** *Scientific Reports* [[paper](https://doi.org/10.1038/s41598-026-63917-x)]
- [2026] **A high-dexterity soft neuroprosthetic hand for daily activities** *Nature Communications* [[paper](https://doi.org/10.1038/s41467-026-75105-6)]
- [2026] **A modular soft gripper with enhanced in-hand manipulation capabilities** *Bioinspiration & Biomimetics* [[paper](https://doi.org/10.1088/1748-3190/ae901e)]
- [2026] **MULTIMODAL TACTILE SENSING FOR CONTACT-RICH ROBOTIC MANIPULATION** *Figshare* [[paper](https://figshare.com/articles/thesis/MULTIMODAL_TACTILE_SENSING_FOR_CONTACT-RICH_ROBOTIC_MANIPULATION/32752281)]
- [2026] **Design and miniaturization of an ultra-fine multi-degree-of-freedom robotic instrument for ophthalmic minimally invasive microsurgery** *ROBOMECH Journal* [[paper](https://doi.org/10.1186/s40648-026-00349-2)]
- [2026] **KISP Hand: Space Gripper for On-Orbit Servicing Missions** *Aerospace* [[paper](https://doi.org/10.3390/aerospace13060513)]
- [2026] **Multimodal Perception Technology, Fusion, and Application of Robot Dexterous Hands for Complex Tasks in Intelligent Manufacturing** *Academic Journal of Science and Technology* [[paper](https://doi.org/10.54097/b88jb554)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Real-World Cooperative Bimanual Dexterous Grasp of Large Objects from Single-View Observations** [[paper](https://arxiv.org/abs/2608.10383)]
- [2026] **G0.5: One Autoregressive Stream for Robot Reasoning and Action** [[paper](https://arxiv.org/abs/2608.11739)]
- [2026] **CMU-Drive and V2V-VLA: Cooperative Multi-agent Unified Driving with Reasoning Benchmark and Vehicle-to-Vehicle Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2608.07621)]
- [2026] **VTAP Gripper: Synergizing Fingertip Sensing and a Visuo-Tactile Active Palm for Dexterous In-Hand Manipulation** [[paper](https://arxiv.org/abs/2607.15448)]
- [2026] **DexVerse: A Modular Benchmark for Multi-Task, Multi-Embodiment Dexterous Manipulation** [[paper](https://arxiv.org/abs/2607.08751)]
- [2026] **Handroid: Bridging Dexterous Hand and Humanoid** [[paper](https://arxiv.org/abs/2607.16187)]
- [2026] **Design and stability analysis of an underactuated hand with passively rotating fingers** [[paper](https://arxiv.org/abs/2607.18950)]
- [2026] **UniCross: Unified Cross-Skill Dexterous Manipulation Synthesis** [[paper](https://arxiv.org/abs/2607.28198)]
- [2026] **HUGS: Guiding Unified Dexterous Grasp Synthesis Across Modes and Scales via Learned Human Priors** [[paper](https://arxiv.org/abs/2607.04554)]
- [2026] **MIDAS Hand: Modular low-Impedance Direct-drive Anthropomorphic Sensing Hand** [[paper](https://arxiv.org/abs/2607.14487)]
- [2026] **DexTele: A Dual-Arm Dexterous Teleoperation System Based on Motion Retargeting and Adaptive Force Control** [[paper](https://arxiv.org/abs/2607.05883)]
- [2026] **TouchWorld: A Predictive and Reactive Tactile Foundation Model for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2607.07287)]
- [2026] **Current as Touch: Proprioceptive Contact Feedback for Compliant Dexterous Manipulation** [[paper](https://arxiv.org/abs/2607.03529)]
- [2026] **Action Chunk Scheduling for Batched Robot Policy Serving** [[paper](https://arxiv.org/abs/2608.00337)]
- [2026] **DSWAM: A Dual-System World Action Foundation Model for Fine-Grained Robot Manipulation** [[paper](https://arxiv.org/abs/2607.04927)]
- [2026] **Closing the Lab-to-Store Gap: A Data-Efficient Post-Training and Experience-Driven Learning VLA Framework for Retail Humanoids** [[paper](https://arxiv.org/abs/2607.20345)]
- [2026] **DynaWM: A Base-VLA-Guided World Foundation Model for Moving-Object Manipulation** [[paper](https://arxiv.org/abs/2607.02604)]
- [2026] **VIA: Visual Interface Agent for Robot Control** [[paper](https://arxiv.org/abs/2607.11119)]
- [2026] **VLA-Corrector: Lightweight Detect-and-Correct Inference for Adaptive Action Horizon** [[paper](https://arxiv.org/abs/2607.01804)]
- [2026] **RoboTTT: Context Scaling for Robot Policies** [[paper](https://arxiv.org/abs/2607.15275)]
- [2026] **TS-Mask VLA: 2D Temporal-Spatial Masking for Vision-Language-Action Model with Effective Bridging** [[paper](https://arxiv.org/abs/2607.09818)]
- [2026] **Artificial Foveated Perception for Mitigating Shortcut Learning in Robotic Foundation Models** [[paper](https://arxiv.org/abs/2607.10655)]
- [2026] **Data Pyramid for Embodied Manipulation: A Survey** [[paper](https://arxiv.org/abs/2607.24744)]
- [2026] **S-squared-VLA: Decoupling Semantic and Spatial Streams in Vision-Language-Action Models for Autonomous Driving** [[paper](https://arxiv.org/abs/2607.13926)]
- [2026] **Designing and Teaching Dexterous Robot Hands** *KiltHub Repository* [[paper](https://doi.org/10.1184/r1/33063809)]
- [2026] **DexGraspDiffuser: Target-Coupled Grasp and Action Diffusion for Dexterous Grasping** *Biomimetics* [[paper](https://doi.org/10.3390/biomimetics11070465)]
- [2026] **A versatile and high-precision robotic gripper with universal applicability** [[paper](https://doi.org/10.1117/12.3119650)]
- [2026] **Mana: Dexterous Manipulation of Articulated Tools** [[paper](https://arxiv.org/abs/2606.13677)]
- [2026] **From Grasps to Dexterity: Large-Scale Grasp Pretraining for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2606.30749)]
- [2026] **CoorDex: Coordinating Body and Hand Priors for Continuous Dexterous Humanoid Loco-Manipulation** [[paper](https://arxiv.org/abs/2606.23680)]
- [2026] **Learning Stable In-Grasp Manipulation in a Non-Dropping Action Space** [[paper](https://arxiv.org/abs/2606.28196)]
- [2026] **Transferring Contact, Not Just Motion: Compliant Grasping Across Dexterous Hands** [[paper](https://arxiv.org/abs/2606.15516)]
- [2026] **NDPP-Grasp: Non-Differentiable Physical Plausibility Constraint-Guided Task-Oriented Dexterous Grasp Generation** [[paper](https://arxiv.org/abs/2606.02432)]
- [2026] **SynManDex: Synthesizing Human-like Dexterous Grasps from Synthetic Human Pre-Grasps** [[paper](https://arxiv.org/abs/2606.09798)]
- [2026] **DexLink Hand: A Compact, Affordable, 16-DOF Linkage-Driven Hand with Human-Like Dexterity** [[paper](https://arxiv.org/abs/2606.17418)]
- [2026] **Grounding Generative Policies in Physics: Optimization-Guided Diffusion for Robot Control** [[paper](https://arxiv.org/abs/2606.24208)]
- [2026] **CoDex: Learning Compositional Dexterous Functional Manipulation without Demonstrations** [[paper](https://arxiv.org/abs/2606.31909)]
- [2026] **DexTeleop-0: Force-Aware Bimanual Dexterous Teleoperation with Ego-Centric Perception towards Shared Autonomy** [[paper](https://arxiv.org/abs/2606.23431)]
- [2026] **DragMesh-2: Physically Plausible Dexterous Hand-Object Interaction with Articulated Objects** [[paper](https://arxiv.org/abs/2606.15133)]
- [2026] **ZeroDex: Zero-Shot Long-Horizon Dexterous Manipulation via Multi-View 3D-Grounded VLM Reasoning** [[paper](https://arxiv.org/abs/2606.19340)]
- [2026] **Blind Dexterous Grasping via Real2Sim2Real Tactile Policy Learning** [[paper](https://arxiv.org/abs/2606.11767)]
- [2026] **Dense Force Estimation with an Event-based Optical Tactile Sensor** [[paper](https://arxiv.org/abs/2606.09451)]
- [2026] **Steering Autoregressive Vision-Language-Action Policies via Action Token Intervention** [[paper](https://arxiv.org/abs/2606.15021)]
- [2026] **Geometric Action Model for Robot Policy Learning** [[paper](https://arxiv.org/abs/2606.17046)]
- [2026] **LaWAM: Latent World Action Models for Efficient Dynamics-Aware Robot Policies** [[paper](https://arxiv.org/abs/2606.15768)]
- [2026] **X-Tokenizer: A Multimodal Action Tokenizer for Vision-Language-Action Pretraining** [[paper](https://arxiv.org/abs/2606.14752)]
- [2026] **Decoupling Semantics and Geometric Grounding: Spatial Visual Prompts for Language-Conditioned Imitation Learning** [[paper](https://arxiv.org/abs/2606.25360)]
- [2026] **NAC: Neural Action Codec for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2606.21372)]
- [2026] **SIMPLE: Simulation-Based Policy Learning and Evaluation for Humanoid Loco-manipulation** [[paper](https://arxiv.org/abs/2606.08278)]
- [2026] **CLASP: Language-Driven Robot Skill Selection and Composition using Task-Parameterized Learning** [[paper](https://arxiv.org/abs/2606.08169)]
- [2026] **VLGA: Vision-Language-Geometry-Action Models for Autonomous Driving** [[paper](https://arxiv.org/abs/2606.12396)]
- [2026] **TAP-VLA: Tactile Annotation Prompting for Vision Language Action Models** [[paper](https://arxiv.org/abs/2606.29089)]
- [2026] **Verifiable Foundation Models for Robot Safety** [[paper](https://arxiv.org/abs/2606.23754)]
- [2026] **VLALeaks: Membership Inference Attacks against Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2606.15165)]
- [2026] **Flow Control: Steering Vision-Language-Action Models with Simple Real-Time Inputs** [[paper](https://arxiv.org/abs/2606.10180)]
- [2026] **RT-VLA: Real-Time Vision-Language-Action Models via Knowledge Distillation** [[paper](https://arxiv.org/abs/2606.14010)]
- [2026] **Universal bioinspired adhesives for arbitrary unknown surfaces toward dexterous robotic manipulation** *Microsystems & Nanoengineering* [[paper](https://doi.org/10.1038/s41378-026-01338-6)]
- [2026] **Play2Perfect: What Matters in Dexterous Play Pretraining for Precise Assembly?** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.26428)]
- [2026] **SECOND-Grasp: Semantic Contact-guided Dexterous Grasping** [[paper](https://arxiv.org/abs/2605.13117)]
- [2026] **Hand-in-the-Loop: Improving VLA Policies for Dexterous Manipulation via Seamless Hand-Arm Intervention** [[paper](https://arxiv.org/abs/2605.15157)]
- [2026] **DexTwist: Dexterous Hand Retargeting for Twist Motion via Mixed Reality-based Teleoperation** [[paper](https://arxiv.org/abs/2605.12182)]
- [2026] **KaRMA: A Kinematic Metric for Fine Manipulation Ability in Robotic Hands** [[paper](https://arxiv.org/abs/2605.15548)]
- [2026] **DexJoCo: A Benchmark and Toolkit for Task-Oriented Dexterous Manipulation on MuJoCo** [[paper](https://arxiv.org/abs/2605.16257)]
- [2026] **DeMaVLA: A Vision-Language-Action Foundation Model for Generalizable Deformable Manipulation** [[paper](https://arxiv.org/abs/2605.31286)]
- [2026] **Qwen-VLA: Unifying Vision-Language-Action Modeling across Tasks, Environments, and Robot Embodiments** [[paper](https://arxiv.org/abs/2605.30280)]
- [2026] **VEGA: Visual Encoder Grounding Alignment for Spatially-Aware Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2605.10485)]
- [2026] **Uni-LaViRA: Language-Vision-Robot Actions Translation for Unified Embodied Navigation** [[paper](https://arxiv.org/abs/2605.27582)]
- [2026] **World Action Models: The Next Frontier in Embodied AI** [[paper](https://arxiv.org/abs/2605.12090)]
- [2026] **Octopus Protocol: One-Shot Hardware Discovery and Control for AI Agents via Infrastructure-as-Prompts** [[paper](https://arxiv.org/abs/2605.09055)]
- [2026] **AT-VLA: Adaptive Tactile Injection for Enhanced Feedback Reaction in Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2605.07308)]
- [2026] **AttenA+: Rectifying Action Inequality in Robotic Foundation Models** [[paper](https://arxiv.org/abs/2605.13548)]
- [2026] **Evo-Depth: A Lightweight Depth-Enhanced Vision-Language-Action Model** [[paper](https://arxiv.org/abs/2605.14950)]
- [2026] **Anticipation-VLA: Solving Long-Horizon Embodied Tasks via Anticipation-based Subgoal Generation** [[paper](https://arxiv.org/abs/2605.01772)]
- [2026] **Fingertip-scale six-axis tactile interface with high-precision force sensing and position localization for dexterous human–machine interactions** *Microsystems & Nanoengineering* [[paper](https://doi.org/10.1038/s41378-026-01292-3)]
- [2026] **Safe and Steerable Geometric Motion Policies for Robotic Dexterous Manipulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2605.21811)]
- [2026] **Virtual reality-enabled embodied intelligence: An adaptive planning method for coordinated dual-arm grasping** *Expert Systems with Applications* [[paper](https://doi.org/10.1016/j.eswa.2026.132714)]
- [2026] **HANDFUL: Sequential Grasp-Conditioned Dexterous Manipulation with Resource Awareness** [[paper](https://arxiv.org/abs/2604.25126)]
- [2026] **HRDexDB: A Paired Human-Robot Dataset for Cross-Embodiment Dexterous Grasping** [[paper](https://arxiv.org/abs/2604.14944)]
- [2026] **A Benchmark of Dexterity for Anthropomorphic Robotic Hands** [[paper](https://arxiv.org/abs/2604.09294)]
- [2026] **Micro-Dexterity in Biological Micromanipulation: Embodiment, Perception, and Control** [[paper](https://arxiv.org/abs/2604.11640)]
- [2026] **BLaDA: Bridging Language to Functional Dexterous Actions within 3DGS Fields** [[paper](https://arxiv.org/abs/2604.08410)]
- [2026] **GraspSense: Physically Grounded Grasp and Grip Planning for a Dexterous Robotic Hand via Language-Guided Perception and Force Maps** [[paper](https://arxiv.org/abs/2604.05697)]
- [2026] **Learning Dexterous Grasping from Sparse Taxonomy Guidance** [[paper](https://arxiv.org/abs/2604.04138)]
- [2026] **BiDexGrasp: Coordinated Bimanual Dexterous Grasps across Object Geometries and Sizes** [[paper](https://arxiv.org/abs/2604.06589)]
- [2026] **SpaceDex: Generalizable Dexterous Grasping in Tiered Workspaces** [[paper](https://arxiv.org/abs/2604.17888)]
- [2026] **Function-based Parametric Co-Design Optimization of Dexterous Hands** [[paper](https://arxiv.org/abs/2604.27557)]
- [2026] **JoyAI-RA 0.1: A Foundation Model for Robotic Autonomy** [[paper](https://arxiv.org/abs/2604.20100)]
- [2026] **PRTS: A Primitive Reasoning and Tasking System via Contrastive Representations** [[paper](https://arxiv.org/abs/2604.27472)]
- [2026] **PokeVLA: Empowering Pocket-Sized Vision-Language-Action Model with Comprehensive World Knowledge Guidance** [[paper](https://arxiv.org/abs/2604.20834)]
- [2026] **V-CAGE: Vision-Closed-Loop Agentic Generation Engine for Robotic Manipulation** [[paper](https://arxiv.org/abs/2604.09036)]
- [2026] **StarVLA: A Lego-like Codebase for Vision-Language-Action Model Developing** [[paper](https://arxiv.org/abs/2604.05014)]
- [2026] **Vision-and-Language Navigation for UAVs: Progress, Challenges, and a Research Roadmap** [[paper](https://arxiv.org/abs/2604.13654)]
- [2026] **AsyncShield: A Plug-and-Play Edge Adapter for Asynchronous Cloud-based VLA Navigation** [[paper](https://arxiv.org/abs/2604.24086)]
- [2026] **LARY: A Latent Action Representation Yielding Benchmark for Generalizable Vision-to-Action Alignment** [[paper](https://arxiv.org/abs/2604.11689)]
- [2026] **Vision-Language-Action Jump-Starting for Reinforcement Learning Robotic Agents** [[paper](https://arxiv.org/abs/2604.13733)]
- [2026] **Vision-Language-Action Safety: Threats, Challenges, Evaluations, and Mechanisms** [[paper](https://arxiv.org/abs/2604.23775)]
- [2026] **Can Explicit Physical Feasibility Benefit VLA Learning? An Empirical Study** [[paper](https://arxiv.org/abs/2604.17896)]
- [2026] **ETac: A Lightweight and Efficient Tactile Simulation Framework for Learning Dexterous Manipulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.20295)]
- [2026] **Embedded Haptic Control for Robotic Grasping using a Tactile Sensor System** *reposiTUm (TU Wien)* [[paper](https://doi.org/10.34749/3061-1466.2026.16)]
- [2026] **FastGrasp: Learning-based Whole-body Control method for Fast Dexterous Grasping with Mobile Manipulators** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.12879)]
- [2026] **Multimodal Quad‐Finger Soft Robotic Hand With Dual‐Chamber Origami Actuator for Large‐Workspace Manipulation** *Advanced Intelligent Systems* [[paper](https://doi.org/10.1002/aisy.70388)]
- [2026] **AdaClearGrasp: Learning Adaptive Clearing for Zero-Shot Robust Dexterous Grasping in Densely Cluttered Environments** [[paper](https://arxiv.org/abs/2603.10616)]
- [2026] **End-to-End Dexterous Grasp Learning from Single-View Point Clouds via a Multi-Object Scene Dataset** [[paper](https://arxiv.org/abs/2603.15410)]
- [2026] **Concurrent Prehensile and Nonprehensile Manipulation: A Practical Approach to Multi-Stage Dexterous Tasks** [[paper](https://arxiv.org/abs/2603.11655)]
- [2026] **UltraDexGrasp: Learning Universal Dexterous Grasping for Bimanual Robots with Synthetic Data** [[paper](https://arxiv.org/abs/2603.05312)]
- [2026] **TEGA: A Tactile-Enhanced Grasping Assistant for Assistive Robotics via Sensor Fusion and Closed-Loop Haptic Feedback** [[paper](https://arxiv.org/abs/2603.05552)]
- [2026] **A Sensorless, Inherently Compliant Anthropomorphic Musculoskeletal Hand Driven by Electrohydraulic Actuators** [[paper](https://arxiv.org/abs/2603.24357)]
- [2026] **Characterization, Analytical Planning, and Hybrid Force Control for the Inspire RH56DFX Hand** [[paper](https://arxiv.org/abs/2603.08988)]
- [2026] **DexDrummer: In-Hand, Contact-Rich, and Long-Horizon Dexterous Robot Drumming** [[paper](https://arxiv.org/abs/2603.22263)]
- [2026] **A Novel Reconfigurable Dexterous Hand Based on Triple-Symmetric Bricard Parallel Mechanism** [[paper](https://arxiv.org/abs/2603.00892)]
- [2026] **Robotic Dexterous Manipulation via Anisotropic Friction Modulation using Passive Rollers** [[paper](https://arxiv.org/abs/2603.27452)]
- [2026] **Which Reconstruction Model Should a Robot Use? Routing Image-to-3D Models for Cost-Aware Robotic Manipulation** [[paper](https://arxiv.org/abs/2603.27797)]
- [2026] **Tele-Catch: Adaptive Teleoperation for Dexterous Dynamic 3D Object Catching** [[paper](https://arxiv.org/abs/2603.28427)]
- [2026] **Contact-Grounded Policy: Dexterous Visuotactile Policy with Generative Contact Grounding** [[paper](https://arxiv.org/abs/2603.05687)]
- [2026] **HapticVLA: Contact-Rich Manipulation via Vision-Language-Action Model without Inference-Time Tactile Sensing** [[paper](https://arxiv.org/abs/2603.15257)]
- [2026] **PHANTOM Hand** [[paper](https://arxiv.org/abs/2603.23152)]
- [2026] **APPLV: Adaptive Planner Parameter Learning from Vision-Language-Action Model** [[paper](https://arxiv.org/abs/2603.08862)]
- [2026] **SELF-VLA: A Skill Enhanced Agentic Vision-Language-Action Framework for Contact-Rich Disassembly** [[paper](https://arxiv.org/abs/2603.11080)]
- [2026] **SABER: A Stealthy Agentic Black-Box Attack Framework for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2603.24935)]
- [2026] **Safe-Night VLA: Seeing the Unseen via Thermal-Perceptive Vision-Language-Action Models for Safety-Critical Manipulation** [[paper](https://arxiv.org/abs/2603.05754)]
- [2026] **NS-VLA: Towards Neuro-Symbolic Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2603.09542)]
- [2026] **Cross-Hand Latent Representation for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2603.10158)]
- [2026] **KineVLA: Towards Kinematics-Aware Vision-Language-Action Models with Bi-Level Action Decomposition** [[paper](https://arxiv.org/abs/2603.17524)]
- [2026] **PhysiFlow: Physics-Aware Humanoid Whole-Body VLA via Multi-Brain Latent Flow Matching and Robust Tracking** [[paper](https://arxiv.org/abs/2603.05410)]
- [2026] **MMaDA-VLA: Large Diffusion Vision-Language-Action Model with Unified Multi-Modal Instruction and Generation** [[paper](https://arxiv.org/abs/2603.25406)]
- [2026] **DyQ-VLA: Temporal-Dynamic-Aware Quantization for Embodied Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2603.07904)]
- [2026] **Towards Affordance-Aware Robotic Dexterous Grasping with Human-like Priors** *Proceedings of the AAAI Conference on Artificial Intelligence* [[paper](https://doi.org/10.1609/aaai.v40i15.38313)]
- [2026] **WGrasp: A Universal Dexterous Grasping Framework Guided by Vision and Tactile Perception** [[paper](https://doi.org/10.1109/aaiml67890.2026.11498158)]
- [2026] **Grasping by interconnection: robust manipulation with minimal object information** *ORBi (University of Liège)* [[paper](https://orbi.uliege.be/handle/2268/341416)]
- [2026] **Ruka-v2: Tendon Driven Open-Source Dexterous Hand with Wrist and Abduction for Robot Learning** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.26660)]
- [2026] **Grasp to Act: Dexterous Grasping for Tool Use in Dynamic Settings** [[paper](https://arxiv.org/abs/2602.20466)]
- [2026] **DexRepNet++: Learning Dexterous Robotic Manipulation with Geometric and Spatial Hand-Object Representations** [[paper](https://arxiv.org/abs/2602.21811)]
- [2026] **Dexterous Manipulation Policies from RGB Human Videos via 3D Hand-Object Trajectory Reconstruction** [[paper](https://arxiv.org/abs/2602.09013)]
- [2026] **One Hand to Rule Them All: Canonical Representations for Unified Dexterous Manipulation** [[paper](https://arxiv.org/abs/2602.16712)]
- [2026] **SimToolReal: An Object-Centric Policy for Zero-Shot Dexterous Tool Manipulation** [[paper](https://arxiv.org/abs/2602.16863)]
- [2026] **DigiArm: An Anthropomorphic 3D-Printed Prosthetic Hand with Enhanced Dexterity for Typing Tasks** [[paper](https://arxiv.org/abs/2602.23017)]
- [2026] **SERNF: Sample-Efficient Real-World Dexterous Policy Fine-Tuning via Action-Chunked Critics and Normalizing Flows** [[paper](https://arxiv.org/abs/2602.09580)]
- [2026] **WHED: A Wearable Hand Exoskeleton for Natural, High-Quality Demonstration Collection** [[paper](https://arxiv.org/abs/2602.17908)]
- [2026] **HoloBrain-0 Technical Report** [[paper](https://arxiv.org/abs/2602.12062)]
- [2026] **GeneralVLA: Generalizable Vision-Language-Action Models with Knowledge-Guided Trajectory Planning** [[paper](https://arxiv.org/abs/2602.04315)]
- [2026] **The Price Is Not Right: Neuro-Symbolic Methods Outperform VLAs on Structured Long-Horizon Manipulation Tasks with Significantly Lower Energy Consumption** [[paper](https://arxiv.org/abs/2602.19260)]
- [2026] **Force Generative Imitation Learning: Bridging Position Trajectory and Force Commands through Control Technique** [[paper](https://arxiv.org/abs/2602.06620)]
- [2026] **RDT2: Exploring the Scaling Limit of UMI Data Towards Zero-Shot Cross-Embodiment Generalization** [[paper](https://arxiv.org/abs/2602.03310)]
- [2026] **Are Foundation Models the Route to Full-Stack Transfer in Robotics?** [[paper](https://arxiv.org/abs/2602.22001)]
- [2026] **Scaling World Model for Hierarchical Manipulation Policies** [[paper](https://arxiv.org/abs/2602.10983)]
- [2026] **Latent Reasoning VLA: Latent Thinking and Prediction for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2602.01166)]
- [2026] **Task-oriented grasping for dexterous robots using postural synergies and reinforcement learning** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2602.20915)]
- [2026] **Generalization of finger-joint kinematics for cleaning tasks** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1725261)]
- [2026] **DextER: Language-driven Dexterous Grasp Generation with Embodied Reasoning** [[paper](https://arxiv.org/abs/2601.16046)]
- [2026] **TOSC: Task-Oriented Shape Completion for Open-World Dexterous Grasp Generation from Partial Point Clouds** [[paper](https://arxiv.org/abs/2601.05499)]
- [2026] **Generate, Transfer, Adapt: Learning Functional Dexterous Grasping from a Single Human Demonstration** [[paper](https://arxiv.org/abs/2601.05243)]
- [2026] **FSAG: Enhancing Human-to-Dexterous-Hand Finger-Specific Affordance Grounding via Diffusion Models** [[paper](https://arxiv.org/abs/2601.08246)]
- [2026] **Closing the Reality Gap: Zero-Shot Sim-to-Real Deployment for Dexterous Force-Based Grasping and Manipulation** [[paper](https://arxiv.org/abs/2601.02778)]
- [2026] **CADGrasp: Learning Contact and Collision Aware General Dexterous Grasping in Cluttered Scenes** [[paper](https://arxiv.org/abs/2601.15039)]
- [2026] **FlyAware: Inertia-Aware Aerial Manipulation via Vision-Based Estimation and Post-Grasp Adaptation** [[paper](https://arxiv.org/abs/2601.22686)]
- [2026] **A Pragmatic VLA Foundation Model** [[paper](https://arxiv.org/abs/2601.18692)]
- [2026] **CompliantVLA-adaptor: VLM-Guided Variable Impedance Action for Safe Contact-Rich Manipulation** [[paper](https://arxiv.org/abs/2601.15541)]
- [2026] **V-VLAPS: Value-Guided Planning for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2601.00969)]
- [2026] **SA-VLA: Spatially-Aware Flow-Matching for Vision-Language-Action Reinforcement Learning** [[paper](https://arxiv.org/abs/2602.00743)]

##### 2025

- [2025] **Universal Dexterous Functional Grasping via Demonstration-Editing Reinforcement Learning** [[paper](https://arxiv.org/abs/2512.13380)]
- [2025] **Vision-Guided Grasp Planning for Prosthetic Hands in Unstructured Environments** [[paper](https://arxiv.org/abs/2512.06517)]
- [2025] **OmniDexVLG: Learning Dexterous Grasp Generation from Vision Language Model-Guided Grasp Semantics, Taxonomy and Functional Affordance** [[paper](https://arxiv.org/abs/2512.03874)]
- [2025] **Development of a 15-Degree-of-Freedom Bionic Hand with Cable-Driven Transmission and Distributed Actuation** [[paper](https://arxiv.org/abs/2512.04399)]
- [2025] **Large Video Planner Enables Generalizable Robot Control** [[paper](https://arxiv.org/abs/2512.15840)]
- [2025] **Safe Learning for Contact-Rich Robot Tasks: A Survey from Classical Learning-Based Methods to Safe Foundation Models** [[paper](https://arxiv.org/abs/2512.11908)]
- [2025] **GR-RL: Going Dexterous and Precise for Long-Horizon Robotic Manipulation** [[paper](https://arxiv.org/abs/2512.01801)]
- [2025] **Point What You Mean: Visually Grounded Instruction Policy** [[paper](https://arxiv.org/abs/2512.18933)]
- [2025] **ZeroDexGrasp: Zero-Shot Task-Oriented Dexterous Grasp Synthesis with Prompt-Based Multi-Stage Semantic Reasoning** [[paper](https://arxiv.org/abs/2511.13327)]
- [2025] **Development of the Bioinspired Tendon-Driven DexHand 021 with Proprioceptive Compliance Control** [[paper](https://arxiv.org/abs/2511.03481)]
- [2025] **Design of an Adaptive Modular Anthropomorphic Dexterous Hand for Human-like Manipulation** [[paper](https://arxiv.org/abs/2511.22100)]
- [2025] **Lightning Grasp: High Performance Procedural Grasp Synthesis with Contact Fields** [[paper](https://arxiv.org/abs/2511.07418)]
- [2025] **From Power to Precision: Learning Fine-grained Dexterity for Multi-fingered Robotic Hands** [[paper](https://arxiv.org/abs/2511.13710)]
- [2025] **ScaleADFG: Affordance-based Dexterous Functional Grasping via Scalable Dataset** [[paper](https://arxiv.org/abs/2511.09602)]
- [2025] **Dexterous Manipulation Transfer via Progressive Kinematic-Dynamic Alignment** [[paper](https://arxiv.org/abs/2511.10987)]
- [2025] **METIS: Multi-Source Egocentric Training for Integrated Dexterous Vision-Language-Action Model** [[paper](https://arxiv.org/abs/2511.17366)]
- [2025] **EveryDayVLA: A Vision-Language-Action Model for Affordable Robotic Manipulation** [[paper](https://arxiv.org/abs/2511.05397)]
- [2025] **Experiences from Benchmarking Vision-Language-Action Models for Robotic Manipulation** [[paper](https://arxiv.org/abs/2511.11298)]
- [2025] **MAP-VLA: Memory-Augmented Prompting for Vision-Language-Action Model in Robotic Manipulation** [[paper](https://arxiv.org/abs/2511.09516)]
- [2025] **OmniVLA: Physically-Grounded Multimodal VLA with Unified Multi-Sensor Perception for Robotic Manipulation** [[paper](https://arxiv.org/abs/2511.01210)]
- [2025] **Towards Deploying VLA without Fine-Tuning: Plug-and-Play Inference-Time VLA Policy Steering via Embodied Evolutionary Diffusion** [[paper](https://arxiv.org/abs/2511.14178)]
- [2025] **10 Open Challenges Steering the Future of Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2511.05936)]
- [2025] **RobotSeg: A Model and Dataset for Segmenting Robots in Image and Video** [[paper](https://arxiv.org/abs/2511.22950)]
- [2025] **OmniDexGrasp: Generalizable Dexterous Grasping via Foundation Model and Force Feedback** [[paper](https://arxiv.org/abs/2510.23119)]
- [2025] **T(R,O) Grasp: Efficient Graph Diffusion of Robot-Object Spatial Transformation for Cross-Embodiment Dexterous Grasping** [[paper](https://arxiv.org/abs/2510.12724)]
- [2025] **SynHLMA:Synthesizing Hand Language Manipulation for Articulated Object with Discrete Human Object Interaction Representation** [[paper](https://arxiv.org/abs/2510.25268)]
- [2025] **SutureBot: A Precision Framework &amp; Benchmark For Autonomous End-to-End Suturing** [[paper](https://arxiv.org/abs/2510.20965)]
- [2025] **Whole-Body Proprioceptive Morphing: A Modular Soft Gripper for Robust Cross-Scale Grasping** [[paper](https://arxiv.org/abs/2510.27666)]
- [2025] **SpikeATac: A Multimodal Tactile Finger with Taxelized Dynamic Sensing for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2510.27048)]
- [2025] **Learning to Grasp Anything by Playing with Random Toys** [[paper](https://arxiv.org/abs/2510.12866)]
- [2025] **HyperVLA: Efficient Inference in Vision-Language-Action Models via Hypernetworks** [[paper](https://arxiv.org/abs/2510.04898)]
- [2025] **GigaBrain-0: A World Model-Powered Vision-Language-Action Model** [[paper](https://arxiv.org/abs/2510.19430)]
- [2025] **Spatial Forcing: Implicit Spatial Representation Alignment for Vision-language-action Model** [[paper](https://arxiv.org/abs/2510.12276)]
- [2025] **BLM$_1$: A Boundless Large Model for Cross-Space, Cross-Task, and Cross-Embodiment Learning** [[paper](https://arxiv.org/abs/2510.24161)]
- [2025] **Dexbotic: Open-Source Vision-Language-Action Toolbox** [[paper](https://arxiv.org/abs/2510.23511)]
- [2025] **A Survey on Efficient Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2510.24795)]
- [2025] **QDepth-VLA: Quantized Depth Prediction as Auxiliary Supervision for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2510.14836)]
- [2025] **X-VLA: Soft-Prompted Transformer as Scalable Cross-Embodiment Vision-Language-Action Model** [[paper](https://arxiv.org/abs/2510.10274)]
- [2025] **Beyond Anthropomorphism: Enhancing Grasping and Eliminating a Degree of Freedom by Fusing the Abduction of Digits Four and Five** [[paper](https://arxiv.org/abs/2509.13074)]
- [2025] **GES-UniGrasp: A Two-Stage Dexterous Grasping Strategy With Geometry-Based Expert Selection** [[paper](https://arxiv.org/abs/2509.23567)]
- [2025] **Learning Geometry-Aware Nonprehensile Pushing and Pulling with Dexterous Hands** [[paper](https://arxiv.org/abs/2509.18455)]
- [2025] **DemoGrasp: Universal Dexterous Grasping from a Single Demonstration** [[paper](https://arxiv.org/abs/2509.22149)]
- [2025] **CEDex: Cross-Embodiment Dexterous Grasp Generation at Scale from Human-like Contact Representations** [[paper](https://arxiv.org/abs/2509.24661)]
- [2025] **Imitation-Guided Bimanual Planning for Stable Manipulation under Changing External Forces** [[paper](https://arxiv.org/abs/2509.19261)]
- [2025] **D3Grasp: Diverse and Deformable Dexterous Grasping for General Objects** [[paper](https://arxiv.org/abs/2509.19892)]
- [2025] **Suction Leap-Hand: Suction Cups on a Multi-fingered Hand Enable Embodied Dexterity and In-Hand Teleoperation** [[paper](https://arxiv.org/abs/2509.20646)]
- [2025] **OmniVLA: An Omni-Modal Vision-Language-Action Model for Robot Navigation** [[paper](https://arxiv.org/abs/2509.19480)]
- [2025] **UnderwaterVLA: Dual-brain Vision-Language-Action architecture for Autonomous Underwater Navigation** [[paper](https://arxiv.org/abs/2509.22441)]
- [2025] **Focusing on What Matters: Object-Agent-centric Tokenization for Vision Language Action models** [[paper](https://arxiv.org/abs/2509.23655)]
- [2025] **GraspQP: Differentiable Optimization of Force Closure for Diverse and Robust Dexterous Grasping** [[paper](https://arxiv.org/abs/2508.15002)]
- [2025] **Survey of Vision-Language-Action Models for Embodied Manipulation** [[paper](https://arxiv.org/abs/2508.15201)]
- [2025] **Mechanistic interpretability for steering vision-language-action models** [[paper](https://arxiv.org/abs/2509.00328)]
- [2025] **EO-1: An Open Unified Embodied Foundation Model for General Robot Control** [[paper](https://arxiv.org/abs/2508.21112)]

[⬆ Back to top](#paper-list)

#### Application

##### 2026

- [2026] **Hong Kong Operation Robot for Chang‘E-8 Mission** [[paper](https://doi.org/10.5194/epsc2026-1285)]
- [2026] **Soft Pop-up Serial Robot with Cable-Hydraulic Hybrid Actuation for Advanced Endoscopy** [[paper](https://doi.org/10.1109/robosoft67810.2026.11522891)]

[⬆ Back to top](#paper-list)

#### Development

##### 2026

- [2026] **Strong yet backdrivable robots through capstan-amplified electroadhesive clutches** *npj Robotics* [[paper](https://doi.org/10.1038/s44182-026-00084-1)]

[⬆ Back to top](#paper-list)

#### Systems & Technology

##### 2026

- [2026] **Helix-coupled spherical joint for anthropomorphic CMC dexterity in robotic hands: Achieving three trajectories with one actuator** *Sensors and Actuators A Physical* [[paper](https://doi.org/10.1016/j.sna.2026.118178)]

[⬆ Back to top](#paper-list)

### Locomotion & Mobility

#### Theory

##### 2026

- [2026] **Locomotion on three legs: the tripedal gaits of canine amputees** [[paper](https://doi.org/10.52843/cassyni.tcr2v6)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Spatiotemporal Agility: Time-Constrained Reinforcement Learning for Vision-Guided Dynamic Quadrupedal Interception** [[paper](https://arxiv.org/abs/2608.06907)]
- [2026] **Learning Fault-Tolerant Locomotion with Adaptive Gait Timing** [[paper](https://arxiv.org/abs/2608.07328)]
- [2026] **Towards Torque-Driven Reinforcement Learning for Quadruped Locomotion** [[paper](https://arxiv.org/abs/2607.18365)]
- [2026] **Isaac Sim-to-Real: Reinforcement Learning based Locomotion for Quadrupeds** [[paper](https://arxiv.org/abs/2607.18135)]
- [2026] **Robust bipedal locomotion on flowable slopes via foot-driven terrain manipulation** [[paper](https://arxiv.org/abs/2607.11855)]
- [2026] **DASH Robot: Minimalistic Design and Optimal Aerial-Terrestrial Locomotion via Contact-Implicit Control** [[paper](https://arxiv.org/abs/2607.18527)]
- [2026] **SKooP: Symmetric Koopman Predictions for Faster and More Generalizable Legged Robot Locomotion with Reinforcement Learning** [[paper](https://arxiv.org/abs/2607.11624)]
- [2026] **Chalito: An Extensible Library for Filtering-Based State Estimation in Quadruped Robots** [[paper](https://arxiv.org/abs/2607.09968)]
- [2026] **Robust Fall Recovery for Armless Bipedal-Wheeled Robots Via Force-Guided Learning** [[paper](https://arxiv.org/abs/2606.14270)]
- [2026] **KYON: Semi-Modular Wheel-Legged Quadruped With Agile Bimanual Capability** [[paper](https://arxiv.org/abs/2606.30243)]
- [2026] **Long-Distance Real-World Navigation of the Legged-Wheeled Robot Go2-W Using Deep Reinforcement Learning** [[paper](https://arxiv.org/abs/2606.21387)]
- [2026] **Sensor Configuration Matters: A Systematic Evaluation of Multimodal SLAM on Quadruped Robots** [[paper](https://arxiv.org/abs/2606.19067)]
- [2026] **SlipSense: Multimodal Sensing for Online Slip Detection in Legged Robots** [[paper](https://arxiv.org/abs/2606.24350)]
- [2026] **X-Morph: Human Motion Priors for Scalable Robot Learning Across Morphologies** [[paper](https://arxiv.org/abs/2606.30290)]
- [2026] **The Quadruped Soft Tail: Compliant Grasping and Swabbing for Contamination Surveys in Harsh Environments** [[paper](https://arxiv.org/abs/2606.30900)]
- [2026] **Online Learning of Robust Legged Odometry with Minimal Exteroceptive Supervision** [[paper](https://arxiv.org/abs/2606.21669)]
- [2026] **A Spiking Neural Architecture for Coordinating Arm and Locomotor Control** [[paper](https://arxiv.org/abs/2606.11034)]
- [2026] **SWAP: Symmetric Equivariant World-Model for Agile Robot Parkour** [[paper](https://arxiv.org/abs/2606.19928)]
- [2026] **Shield-Loco: Shielding Locomotion Policies with Predictive Safety Filtering** [[paper](https://arxiv.org/abs/2606.07193)]
- [2026] **Mixture-of-Experts RL for Fault-Tolerant Legged Locomotion** [[paper](https://arxiv.org/abs/2606.25965)]
- [2026] **Locomotion analysis of a quadruped interacting with the lunar granular surface** [[paper](https://arxiv.org/abs/2606.10273)]
- [2026] **Mobile Pedipulation for Object Sliding via Hierarchical Control on a Wheeled Bipedal Robot** [[paper](https://arxiv.org/abs/2606.19233)]
- [2026] **Learning to Balance Motor Thermal Safety and Quadrupedal Locomotion Performance with Residual Policy** [[paper](https://arxiv.org/abs/2605.27046)]
- [2026] **Energy-Efficient Quadruped Locomotion with Compliant Feet** [[paper](https://arxiv.org/abs/2605.14411)]
- [2026] **Towards Low-Gravity Planetary Exploration using Reinforcement Learning for Walking, Jumping, and In-flight Attitude Control** [[paper](https://arxiv.org/abs/2605.24643)]
- [2026] **Learning Dynamic Pick-and-Place for a Legged Manipulator** [[paper](https://arxiv.org/abs/2605.15713)]
- [2026] **WiXus: A Wheeled-Legged Robot with Wire-Driven Environmental Utilizing to Integrate Mobility and Manipulation** [[paper](https://arxiv.org/abs/2605.20932)]
- [2026] **Neuromorphic Reinforcement Learning for Quadruped Locomotion Control on Uneven Terrain** [[paper](https://arxiv.org/abs/2605.09595)]
- [2026] **MUJICA: Multi-skill Unified Joint Integration of Control Architecture for Wheeled-Legged Robots** [[paper](https://arxiv.org/abs/2605.13058)]
- [2026] **Evaluation of an Actuated Spine in Agile Quadruped Locomotion** [[paper](https://arxiv.org/abs/2605.07988)]
- [2026] **Motion Design for Grasp-Based Dynamic Locomotion in Microgravity** [[paper](https://arxiv.org/abs/2605.21704)]
- [2026] **Simulator Adaptation for Sim-to-Real Learning of Legged Locomotion via Proprioceptive Distribution Matching** [[paper](https://arxiv.org/abs/2604.11090)]
- [2026] **Bipedal-Walking-Dynamics Model on Granular Terrains** [[paper](https://arxiv.org/abs/2604.11981)]
- [2026] **X2-N: A Transformable Wheel-legged Humanoid Robot with Dual-mode Locomotion and Manipulation** [[paper](https://arxiv.org/abs/2604.21541)]
- [2026] **A Foot Resistive Force Model for Legged Locomotion on Muddy Terrains** [[paper](https://arxiv.org/abs/2604.12006)]
- [2026] **A Survey of Legged Robotics in Non-Inertial Environments: Past, Present, and Future** [[paper](https://arxiv.org/abs/2604.20990)]
- [2026] **ContractionPPO: Certified Reinforcement Learning via Differentiable Contraction Layers** [[paper](https://arxiv.org/abs/2603.19632)]
- [2026] **MiNI-Q: A Miniature, Wire-Free Quadruped with Unbounded, Independently Actuated Leg Joints** [[paper](https://arxiv.org/abs/2603.11537)]
- [2026] **Energy Prediction on Sloping Ground for Quadruped Robots** [[paper](https://arxiv.org/abs/2603.11963)]
- [2026] **Safe Whole-Body Loco-Manipulation via Combined Model and Learning-based Control** [[paper](https://arxiv.org/abs/2603.02443)]
- [2026] **Panoramic Multimodal Semantic Occupancy Prediction for Quadruped Robots** [[paper](https://arxiv.org/abs/2603.13108)]
- [2026] **VIP-Loco: A Visually Guided Infinite Horizon Planning Framework for Legged Locomotion** [[paper](https://arxiv.org/abs/2603.14345)]
- [2026] **BinWalker: Development and Field Evaluation of a Quadruped Manipulator Platform for Sustainable Litter Collection** [[paper](https://arxiv.org/abs/2603.10529)]
- [2026] **Dynamic Modeling and Attitude Control of a Reaction-Wheel-Based Low-Gravity Bipedal Hopper** [[paper](https://arxiv.org/abs/2603.10670)]
- [2026] **SteadyTray: Learning Object Balancing Tasks in Humanoid Tray Transport via Residual Reinforcement Learning** [[paper](https://arxiv.org/abs/2603.10306)]
- [2026] **Learning Whole-Body Control for a Salamander Robot** [[paper](https://arxiv.org/abs/2603.16683)]
- [2026] **Jumping in legged robots: A review of advances in jumping abilities, methods, challenges, and future directions** *Robotics and Autonomous Systems* [[paper](https://doi.org/10.1016/j.robot.2026.105434)]
- [2026] **Agile asymmetric multi-legged locomotion: contact planning via geometric mechanics and spin model duality** [[paper](https://arxiv.org/abs/2602.09123)]
- [2026] **Dynamic Modeling and MPC for Locomotion of Tendon-Driven Soft Quadruped** [[paper](https://arxiv.org/abs/2602.16371)]
- [2026] **Enhancing Navigation Efficiency of Quadruped Robots via Leveraging Personal Transportation Platforms** [[paper](https://arxiv.org/abs/2602.03397)]
- [2026] **Soft Surfaced Vision-Based Tactile Sensing for Bipedal Robot Applications** [[paper](https://arxiv.org/abs/2602.18638)]
- [2026] **Biomechanical Comparisons Reveal Divergence of Human and Humanoid Gaits** [[paper](https://arxiv.org/abs/2602.21666)]
- [2026] **Phase-Aware Policy Learning for Skateboard Riding of Quadruped Robots via Feature-wise Linear Modulation** [[paper](https://arxiv.org/abs/2602.09370)]
- [2026] **TOLEBI: Learning Fault-Tolerant Bipedal Locomotion via Online Status Estimation and Fallibility Rewards** [[paper](https://arxiv.org/abs/2602.05596)]
- [2026] **Jumping Control for a Quadrupedal Wheeled-Legged Robot via NMPC and DE Optimization** [[paper](https://arxiv.org/abs/2602.21612)]
- [2026] **LocoVLM: Grounding Vision and Language for Adapting Versatile Legged Locomotion Policies** [[paper](https://arxiv.org/abs/2602.10399)]
- [2026] **Contact-Anchored Proprioceptive Odometry for Legged and Wheel-Legged Robots** [[paper](https://arxiv.org/abs/2602.17393)]
- [2026] **Scout-Rover cooperation: online terrain strength mapping and traversal risk estimation for planetary-analog explorations** [[paper](https://arxiv.org/abs/2602.18688)]
- [2026] **Self-Supervised Bootstrapping of Action-Predictive Embodied Reasoning** [[paper](https://arxiv.org/abs/2602.08167)]
- [2026] **Training and Simulation of Quadrupedal Robot in Adaptive Stair Climbing and Descending for Indoor Firefighting: An End-to-End Reinforcement Learning Approach** [[paper](https://arxiv.org/abs/2602.03087)]
- [2026] **SENSE-STEP: Learning Sim-to-Real Locomotion for a Sensory-Enabled Soft Quadruped Robot** [[paper](https://arxiv.org/abs/2602.13078)]
- [2026] **Sampling Strategy Design for Model Predictive Path Integral Control on Legged Robot Locomotion** [[paper](https://arxiv.org/abs/2601.01409)]
- [2026] **GPO: Growing Policy Optimization for Legged Robot Locomotion and Whole-Body Control** [[paper](https://arxiv.org/abs/2601.20668)]
- [2026] **AME-2: Agile and Generalized Legged Locomotion via Attention-Based Neural Map Encoding** [[paper](https://arxiv.org/abs/2601.08485)]
- [2026] **PUMA: Perception-driven Unified Foothold Prior for Mobility Augmented Quadruped Parkour** [[paper](https://arxiv.org/abs/2601.15995)]
- [2026] **Efficiently Learning Robust Torque-based Locomotion Through Reinforcement with Model-Based Supervision** [[paper](https://arxiv.org/abs/2601.16109)]
- [2026] **M-SEVIQ: A Multi-band Stereo Event Visual-Inertial Quadruped-based Dataset for Perception under Rapid Motion and Challenging Illumination** [[paper](https://arxiv.org/abs/2601.02777)]

##### 2025

- [2025] **START: Traversing Sparse Footholds with Terrain Reconstruction** [[paper](https://arxiv.org/abs/2512.13153)]
- [2025] **MOBIUS: A Multi-Modal Bipedal Robot that can Walk, Crawl, Climb, and Roll** [[paper](https://arxiv.org/abs/2511.01774)]
- [2025] **Stable and Robust SLIP Model Control via Energy Conservation-Based Feedback Cancellation for Quadrupedal Applications** [[paper](https://arxiv.org/abs/2511.05402)]
- [2025] **Human Imitated Bipedal Locomotion with Frequency Based Gait Generator Network** [[paper](https://arxiv.org/abs/2511.17387)]
- [2025] **X-IONet: Cross-Platform Inertial Odometry Network for Pedestrian and Legged Robot** [[paper](https://arxiv.org/abs/2511.08277)]
- [2025] **DecARt Leg: Design and Evaluation of a Novel Humanoid Robot Leg with Decoupled Actuation for Agile Locomotion** [[paper](https://arxiv.org/abs/2511.10021)]
- [2025] **OmniTrack++: Omnidirectional Multi-Object Tracking by Learning Large-FoV Trajectory Feedback** [[paper](https://arxiv.org/abs/2511.00510)]
- [2025] **Towards An Adaptive Locomotion Strategy For Quadruped Rovers: Quantifying When To Slide Or Walk On Planetary Slopes** [[paper](https://arxiv.org/abs/2510.18678)]
- [2025] **Bridge the Gap: Enhancing Quadruped Locomotion with Vertical Ground Perturbations** [[paper](https://arxiv.org/abs/2510.13488)]
- [2025] **Adaptive Invariant Extended Kalman Filter for Legged Robot State Estimation** [[paper](https://arxiv.org/abs/2510.16755)]
- [2025] **Stand, Walk, Navigate: Recovery-Aware Visual Navigation on a Low-Cost Wheeled Quadruped** [[paper](https://arxiv.org/abs/2510.23902)]
- [2025] **Gain Tuning Is Not What You Need: Reward Gain Adaptation for Constrained Locomotion Learning** [[paper](https://arxiv.org/abs/2510.10759)]
- [2025] **NaviGait: Navigating Dynamically Feasible Gait Libraries using Deep Reinforcement Learning** [[paper](https://arxiv.org/abs/2510.11542)]
- [2025] **Towards Proprioceptive Terrain Mapping with Quadruped Robots for Exploration in Planetary Permanently Shadowed Regions** [[paper](https://arxiv.org/abs/2510.18986)]
- [2025] **Quadrupeds for Planetary Exploration: Field Testing Control Algorithms on an Active Volcano** [[paper](https://arxiv.org/abs/2510.18600)]
- [2025] **Walking, Rolling, and Beyond: First-Principles and RL Locomotion on a TARS-Inspired Robot** [[paper](https://arxiv.org/abs/2510.05001)]
- [2025] **ATRos: Learning Energy-Efficient Agile Locomotion for Wheeled-legged Robots** [[paper](https://arxiv.org/abs/2510.09980)]
- [2025] **Estimation of Minimum Stride Frequency for the Frontal Plane Stability of Bipedal Systems** [[paper](https://arxiv.org/abs/2510.22030)]
- [2025] **SPARC: Spine with Prismatic and Revolute Compliance for Quadruped Robots** [[paper](https://arxiv.org/abs/2510.01984)]
- [2025] **Adaptive Legged Locomotion via Online Learning for Model Predictive Control** [[paper](https://arxiv.org/abs/2510.15626)]
- [2025] **Like Playing a Video Game: Spatial-Temporal Optimization of Foot Trajectories for Controlled Football Kicking in Bipedal Robots** [[paper](https://arxiv.org/abs/2510.01843)]
- [2025] **Dynamic Quadrupedal Legged and Aerial Locomotion via Structure Repurposing** [[paper](https://arxiv.org/abs/2510.09526)]
- [2025] **Real-time Multi-Plane Segmentation Based on GPU Accelerated High-Resolution 3D Voxel Mapping for Legged Robot Locomotion** [[paper](https://arxiv.org/abs/2510.01592)]
- [2025] **An adaptive hierarchical control framework for quadrupedal robots in planetary exploration** [[paper](https://arxiv.org/abs/2510.17249)]
- [2025] **KiVi: Kinesthetic-Visuospatial Integration for Dynamic and Safe Egocentric Legged Locomotion** [[paper](https://arxiv.org/abs/2509.23650)]
- [2025] **Multi-Embodiment Locomotion at Scale with extreme Embodiment Randomization** [[paper](https://arxiv.org/abs/2509.02815)]
- [2025] **RL-augmented Adaptive Model Predictive Control for Bipedal Locomotion over Challenging Terrain** [[paper](https://arxiv.org/abs/2509.18466)]
- [2025] **SAC-Loco: Safe and Adjustable Compliant Quadrupedal Locomotion** [[paper](https://arxiv.org/abs/2509.23223)]
- [2025] **Learning Multi-Skill Legged Locomotion Using Conditional Adversarial Motion Priors** [[paper](https://arxiv.org/abs/2509.21810)]
- [2025] **Acrobotics: A Generalist Approach to Quadrupedal Robots' Parkour** [[paper](https://arxiv.org/abs/2509.02727)]
- [2025] **Efficient Learning-Based Control of a Legged Robot in Lunar Gravity** [[paper](https://arxiv.org/abs/2509.10128)]
- [2025] **LIPM-Guided Reinforcement Learning for Stable and Perceptive Locomotion in Bipedal Robots** [[paper](https://arxiv.org/abs/2509.09106)]
- [2025] **Analysis of Harpy's Constrained Trotting and Jumping Maneuver** [[paper](https://arxiv.org/abs/2508.18139)]
- [2025] **First Order Model-Based RL through Decoupled Backpropagation** [[paper](https://arxiv.org/abs/2509.00215)]

[⬆ Back to top](#paper-list)

#### Application

##### 2026

- [2026] **JitTrack: Onboard Multi-Object Tracking Against Viewpoint Jitter for Agile UAVs** [[paper](https://arxiv.org/abs/2608.10485)]
- [2026] **FAM-DQ: A Dual-Quadrotor-Based Fully Actuated Aerial Manipulator for High-Torque Interaction** [[paper](https://arxiv.org/abs/2608.13220)]
- [2026] **OmniAI: A Surface-Adaptive Aerial Projection Interface for Human--Drone Interaction** [[paper](https://arxiv.org/abs/2608.00721)]
- [2026] **FLOAT Drone for Physical Interaction: Lateral Airflow Reduction, Wrench Modeling, and Adaptive Control** [[paper](https://arxiv.org/abs/2607.04260)]
- [2026] **Vision Language Action (VLA) Models for Unmanned Aerial Robotics and Bimanual Manipulation: A Review** [[paper](https://arxiv.org/abs/2607.06706)]
- [2026] **ActiveFly-Bench: Aligning Embodied Question Answering with Vision-Language-Action for Aerial Embodied Perception** [[paper](https://arxiv.org/abs/2607.10180)]
- [2026] **BC-NMPC: Battery-Constrained NMPC with Propulsion Prediction and Replanning for High-Speed Flight** [[paper](https://arxiv.org/abs/2607.23867)]
- [2026] **Recursive ArUco Markers: A Scalable Fiducial Marker Design for Unmanned Aerial Vehicle Landing Pads** [[paper](https://arxiv.org/abs/2607.13830)]
- [2026] **Improving Autonomous Nano-drones Performance via Automated End-to-End Optimization and Deployment of DNNs** [[paper](https://arxiv.org/abs/2607.12593)]
- [2026] **AeroAct: Action-Centered World-Action Models for Language-Conditioned Quadrotor Flight** [[paper](https://arxiv.org/abs/2607.14997)]
- [2026] **Autonomous Aerial Manipulation via Contextual Contrastive Meta Reinforcement Learning** [[paper](https://arxiv.org/abs/2606.08533)]
- [2026] **Wind and State Estimation on SE(3): Comparative Evaluation of EKF and UKF with Continuous and Discrete Quadrotor Models** [[paper](https://arxiv.org/abs/2606.30804)]
- [2026] **DroneShield-AI: A Multi-Modal Sensor Fusion Framework for Real-Time Autonomous Drone Threat Detection, Behavioral Intent Classification, and Swarm Intelligence in Contested Airspace** [[paper](https://arxiv.org/abs/2606.11687)]
- [2026] **Realtime Wind Estimation using Low Cost Quadrotor Uncrewed Aerial Vehicles** [[paper](https://arxiv.org/abs/2606.30581)]
- [2026] **UGV-Conditioned Multi-UAV Informative Planning on a Shared Exposure Belief** [[paper](https://arxiv.org/abs/2606.12306)]
- [2026] **Market-Based Replanning for Safety-Critical UAV Swarms in Search and Rescue Missions** [[paper](https://arxiv.org/abs/2606.01970)]
- [2026] **LNN-Fly: Continuous-Time UAV Navigation for Robust Obstacle Avoidance under Timing Mismatch** [[paper](https://arxiv.org/abs/2606.28827)]
- [2026] **AerialClaw: An Open-Source Framework for LLM-Driven Autonomous Aerial Agents** [[paper](https://arxiv.org/abs/2606.12142)]
- [2026] **AIR-VLA+: Decoupling Movement and Manipulation via Cascaded Dual-Action Decoders with Asymmetric MoE for Aerial Robots** [[paper](https://arxiv.org/abs/2606.12859)]
- [2026] **AeroCast: Probabilistic 3D Trajectory Prediction for Non-Cooperative Aerial Obstacles via Transformer-MDN Architecture** [[paper](https://arxiv.org/abs/2606.25122)]
- [2026] **Trajectory Optimization in Single and Dual-UAV Bearing-Only Target Localization** [[paper](https://arxiv.org/abs/2606.09188)]
- [2026] **A Progress-Aware Leader-Follower Midair Docking System for Dual-Drone Aerial Manipulation** [[paper](https://arxiv.org/abs/2605.29410)]
- [2026] **LRDDv3: High-Resolution Long-Range Drone Detection Dataset with Range Information and Thermal Data** [[paper](https://arxiv.org/abs/2605.25942)]
- [2026] **HoLoArm: Deformable Arms for Collision-Tolerant Quadrotor Flight** [[paper](https://arxiv.org/abs/2605.25790)]
- [2026] **CosFly: Plan in the Matrix, Fly in the World** [[paper](https://arxiv.org/abs/2605.19120)]
- [2026] **CosFly-Track: A Large-Scale Multi-Modal Dataset for UAV Visual Tracking via Multi-Constraint Trajectory Optimization** [[paper](https://arxiv.org/abs/2605.17776)]
- [2026] **An Aerial Manipulator for Perception-Driven Flower Targeting Toward Contactless Pollination in Vertical Farming** [[paper](https://arxiv.org/abs/2605.06759)]
- [2026] **ESARBench: A Benchmark for Agentic UAV Embodied Search and Rescue** [[paper](https://arxiv.org/abs/2605.01371)]
- [2026] **A Topology-Aware Spatiotemporal Handover Framework for Continuous Multi-UAV Tracking** [[paper](https://arxiv.org/abs/2605.15779)]
- [2026] **Loiter UAV Reinsertion Guidance for Fixed-wing UAV Corridors** [[paper](https://arxiv.org/abs/2605.13822)]
- [2026] **Orientation Matters: Learning Radiation Patterns of Multi-Rotor UAVs In-Flight to Enhance Communication Availability Modeling** [[paper](https://arxiv.org/abs/2604.02827)]
- [2026] **MARS-Dragonfly: Agile and Robust Flight Control of Modular Aerial Robot Systems** [[paper](https://arxiv.org/abs/2604.05499)]
- [2026] **Relative State Estimation using Event-Based Propeller Sensing** [[paper](https://arxiv.org/abs/2604.18289)]
- [2026] **Robust Energy-Aware Routing for Air-Ground Cooperative Multi-UAV Delivery in Wind-Uncertain Environments** [[paper](https://arxiv.org/abs/2604.13441)]
- [2026] **Robust Fleet Sizing for Multi-UAV Inspection Missions under Synchronized Replacement Demand** [[paper](https://arxiv.org/abs/2604.15890)]
- [2026] **Enhancing Drone Light Shows Performances: Optimal Allocation and Trajectories for Swarm Drone Formations** [[paper](https://arxiv.org/abs/2603.24401)]
- [2026] **Fly360: Omnidirectional Obstacle Avoidance within Drone View** [[paper](https://arxiv.org/abs/2603.06573)]
- [2026] **AeroGen: Agentic Drone Autonomy through Single-Shot Structured Prompting &amp; Drone SDK** [[paper](https://arxiv.org/abs/2603.14236)]
- [2026] **Lightweight 3D LiDAR-Based UAV Tracking: An Adaptive Extended Kalman Filtering Approach** [[paper](https://arxiv.org/abs/2603.09783)]
- [2026] **Integrated Multi-Drone Task Allocation, Sequencing, and Optimal Trajectory Generation in Obstacle-Rich 3D Environments** [[paper](https://arxiv.org/abs/2603.24908)]
- [2026] **Agile Interception of a Flying Target using Competitive Reinforcement Learning** [[paper](https://arxiv.org/abs/2603.16279)]
- [2026] **Meta-Adaptive Beam Search Planning for Transformer-Based Reinforcement Learning Control of UAVs with Overhead Manipulators under Flight Disturbances** [[paper](https://arxiv.org/abs/2603.26612)]
- [2026] **Self-supervised Domain Adaptation for Visual 3D Pose Estimation of Nano-drone Racing Gates by Enforcing Geometric Consistency** [[paper](https://arxiv.org/abs/2603.02936)]
- [2026] **Strain-Parameterized Coupled Dynamics and Dual-Camera Visual Servoing for Aerial Continuum Manipulators** [[paper](https://arxiv.org/abs/2603.23333)]
- [2026] **Seeing Where to Deploy: Metric RGB-Based Traversability Analysis for Aerial-to-Ground Hidden Space Inspection** [[paper](https://arxiv.org/abs/2603.14639)]
- [2026] **MiniUGV$_2$: A Compact UAV-Deployable Tracked Ground Vehicle with Manipulation Capabilities** [[paper](https://arxiv.org/abs/2603.00972)]
- [2026] **Learning on the Fly: Replay-Based Continual Object Perception for Indoor Drones** [[paper](https://arxiv.org/abs/2602.13440)]
- [2026] **Acoustic Drone Package Delivery Detection** [[paper](https://arxiv.org/abs/2602.09991)]
- [2026] **Chasing Ghosts: A Simulation-to-Real Olfactory Navigation Stack with Optional Vision Augmentation** [[paper](https://arxiv.org/abs/2602.19577)]
- [2026] **Large-scale Photorealistic Outdoor 3D Scene Reconstruction from UAV Imagery Using Gaussian Splatting Techniques** [[paper](https://arxiv.org/abs/2602.20342)]
- [2026] **From Bench to Flight: Translating Drone Impact Tests into Operational Safety Limits** [[paper](https://arxiv.org/abs/2602.05922)]
- [2026] **SkySim: A ROS2-based Simulation Environment for Natural Language Control of Drone Swarms using Large Language Models** [[paper](https://arxiv.org/abs/2602.01226)]
- [2026] **Large Language Model-Assisted UAV Operations and Communications: A Multifaceted Survey and Tutorial** [[paper](https://arxiv.org/abs/2602.19534)]
- [2026] **EKF-Based Depth Camera and Deep Learning Fusion for UAV-Person Distance Estimation and Following in SAR Operations** [[paper](https://arxiv.org/abs/2602.20958)]
- [2026] **High-Speed Vision-Based Flight in Clutter with Safety-Shielded Reinforcement Learning** [[paper](https://arxiv.org/abs/2602.08653)]
- [2026] **Curriculum Reinforcement Learning for Quadrotor Racing with Random Obstacles** [[paper](https://arxiv.org/abs/2602.24030)]
- [2026] **Bumper Drone: Elastic Morphology Design for Aerial Physical Interaction** [[paper](https://arxiv.org/abs/2602.18976)]
- [2026] **Virtual-Tube-Based Cooperative Transport Control for Multi-UAV Systems in Constrained Environments** [[paper](https://arxiv.org/abs/2602.05516)]
- [2026] **FlyPose: Towards Robust Human Pose Estimation From Aerial Views** [[paper](https://arxiv.org/abs/2601.05747)]
- [2026] **SLAP: Slapband-based Autonomous Perching Drone with Failure Recovery for Vertical Tree Trunks** [[paper](https://arxiv.org/abs/2601.00238)]
- [2026] **Precision Meets Art: Autonomous Multi-UAV System for Large Scale Mural Drawing** [[paper](https://arxiv.org/abs/2601.06508)]
- [2026] **Agentic AI Meets Edge Computing in Autonomous UAV Swarms** [[paper](https://arxiv.org/abs/2601.14437)]
- [2026] **DiffusionCinema: Text-to-Aerial Cinematography** [[paper](https://arxiv.org/abs/2601.17412)]
- [2026] **Exploiting Light To Enhance The Endurance and Navigation of Lighter-Than-Air Micro-Drones** [[paper](https://arxiv.org/abs/2601.13088)]
- [2026] **A Survey of Medical Drones from Flight Dynamics, Guidance, Navigation, and Control Perspectives** [[paper](https://arxiv.org/abs/2602.06969)]
- [2026] **Edge-Optimized Multimodal Learning for UAV Video Understanding via BLIP-2** [[paper](https://arxiv.org/abs/2601.08408)]
- [2026] **AIR-VLA: Vision-Language-Action Systems for Aerial Manipulation** [[paper](https://arxiv.org/abs/2601.21602)]
- [2026] **Perception-to-Pursuit: Track-Centric Temporal Reasoning for Open-World Drone Detection and Autonomous Chasing** [[paper](https://arxiv.org/abs/2601.19318)]
- [2026] **Online parameter estimation for the Crazyflie quadcopter through an EM algorithm** [[paper](https://arxiv.org/abs/2601.17009)]

##### 2025

- [2025] **Global End-Effector Pose Control of an Underactuated Aerial Manipulator via Reinforcement Learning** [[paper](https://arxiv.org/abs/2512.21085)]
- [2025] **VLA-AN: An Efficient and Onboard Vision-Language-Action Framework for Aerial Navigation in Complex Environments** [[paper](https://arxiv.org/abs/2512.15258)]
- [2025] **Field evaluation and optimization of a lightweight autonomous lidar-based UAV system based on a rigorous experimental setup in boreal forest environments** [[paper](https://arxiv.org/abs/2512.14340)]
- [2025] **Heteroscedastic Bayesian Optimization-Based Dynamic PID Tuning for Accurate and Robust UAV Trajectory Tracking** [[paper](https://arxiv.org/abs/2512.24249)]
- [2025] **Optimal Safety-Aware Scheduling for Multi-Agent Aerial 3D Printing with Utility Maximization under Dependency Constraints** [[paper](https://arxiv.org/abs/2512.05815)]
- [2025] **EcoFlight: Finding Low-Energy Paths Through Obstacles for Autonomous Sensing Drones** [[paper](https://arxiv.org/abs/2511.12618)]
- [2025] **OpenVLN: Open-world Aerial Vision-Language Navigation** [[paper](https://arxiv.org/abs/2511.06182)]
- [2025] **Aerial Assistance System for Automated Firefighting during Turntable Ladder Operations** [[paper](https://arxiv.org/abs/2511.14504)]
- [2025] **Optimizing the flight path for a scouting Uncrewed Aerial Vehicle** [[paper](https://arxiv.org/abs/2511.10598)]
- [2025] **AerialMind: Towards Referring Multi-Object Tracking in UAV Scenarios** [[paper](https://arxiv.org/abs/2511.21053)]
- [2025] **RSPECT: Robust and Scalable Planner for Energy-Aware Coordination of UAV-UGV Teams in Aerial Monitoring** [[paper](https://arxiv.org/abs/2511.21957)]
- [2025] **Threat-Aware UAV Dodging of Human-Thrown Projectiles with an RGB-D Camera** [[paper](https://arxiv.org/abs/2511.22847)]
- [2025] **Aerial Image Stitching Using IMU Data from a UAV** [[paper](https://arxiv.org/abs/2511.06841)]
- [2025] **Integration of a Variable Stiffness Link for Long-Reach Aerial Manipulation** [[paper](https://arxiv.org/abs/2510.15639)]
- [2025] **Next-Generation LLM for UAV: From Natural Language to Autonomous Flight** [[paper](https://arxiv.org/abs/2510.21739)]
- [2025] **Autonomous Reactive Masonry Construction using Collaborative Heterogeneous Aerial Robots with Experimental Demonstration** [[paper](https://arxiv.org/abs/2510.15114)]
- [2025] **Performance-Guided Refinement for Visual Aerial Navigation using Editable Gaussian Splatting in FalconGym 2.0** [[paper](https://arxiv.org/abs/2510.02248)]
- [2025] **Coordinated Autonomous Drones for Human-Centered Fire Evacuation in Partially Observable Urban Environments** [[paper](https://arxiv.org/abs/2510.23899)]
- [2025] **Cooperative Guidance for Aerial Defense in Multiagent Systems** [[paper](https://arxiv.org/abs/2510.02087)]
- [2025] **Real-Time Trajectory Generation and Hybrid Lyapunov-Based Control for Hopping Robots** [[paper](https://arxiv.org/abs/2510.01138)]
- [2025] **Remote Autonomy for Multiple Small Lowcost UAVs in GNSS-denied Search and Rescue Operations** [[paper](https://arxiv.org/abs/2510.21357)]
- [2025] **A Modular and Scalable System Architecture for Heterogeneous UAV Swarms Using ROS 2 and PX4-Autopilot** [[paper](https://arxiv.org/abs/2510.27327)]
- [2025] **TACOS: Task Agnostic COordinator of a multi-drone System** [[paper](https://arxiv.org/abs/2510.01869)]
- [2025] **Agentic Aerial Cinematography: From Dialogue Cues to Cinematic Trajectories** [[paper](https://arxiv.org/abs/2509.16176)]
- [2025] **Reinforcement Learning for Autonomous Point-to-Point UAV Navigation** [[paper](https://arxiv.org/abs/2509.13943)]
- [2025] **GLIDE: A Coordinated Aerial-Ground Framework for Search and Rescue in Unknown Environments** [[paper](https://arxiv.org/abs/2509.14210)]
- [2025] **CineWild: Balancing Art and Robotics for Ethical Wildlife Documentary Filmmaking** [[paper](https://arxiv.org/abs/2509.24921)]
- [2025] **Maximizing UAV Cellular Connectivity with Reinforcement Learning for BVLoS Path Planning** [[paper](https://arxiv.org/abs/2509.13336)]
- [2025] **CORB-Planner: Corridor as Observations for RL Planning in High-Speed Flight** [[paper](https://arxiv.org/abs/2509.11240)]
- [2025] **A Survey on LiDAR-based Autonomous Aerial Vehicles** [[paper](https://arxiv.org/abs/2509.10730)]
- [2025] **JuggleRL: Mastering Ball Juggling with a Quadrotor via Deep Reinforcement Learning** [[paper](https://arxiv.org/abs/2509.24892)]

[⬆ Back to top](#paper-list)

#### Development

##### 2026

- [2026] **Agile legged locomotion in reconfigurable modular robots** *Proceedings of the National Academy of Sciences* [[paper](https://doi.org/10.1073/pnas.2519129123)]

[⬆ Back to top](#paper-list)

### Perception & Sensing

#### Theory

##### 2026

- [2026] **Bifurcation-Gated Kresling Origami Triboelectric Mechanoreceptor Enabling Self-Powered Multimodal Tactile Sensing for Intelligent Human-Robot Interaction** *Nano Energy* [[paper](https://doi.org/10.1016/j.nanoen.2026.112280)]
- [2026] **A Fully Silicone Flexible Self-Powered Teng Tactile Skin for Multimodal Sensing and Material Recognition on Robotic Hands** *ECS Meeting Abstracts* [[paper](https://doi.org/10.1149/ma2026-01341594mtgabs)]
- [2026] **Flexible 3D Tactile Sensor With Cube‐Shaped Microstructure for Multimodal Force‐Temperature Decoupled Perception for Soft Robotic Hands** *Advanced Sensor Research* [[paper](https://doi.org/10.1002/adsr.202600003)]
- [2026] **Intrinsic Force–TemperatureSelf-DecouplingEnables Human-like Tactile Sensing in a Soft Ionic Skin** *ACS Nano* [[paper](https://doi.org/10.1021/acsnano.6c09063)]
- [2026] **Object Shape Recognition Using Sparse Soft Capacitive Tactile Sensors for Robotic Hands** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202607.0606.v1)]
- [2026] **Tactile electronic skin: From mechanical perception to intelligent interfaces** *Sensors and Actuators A Physical* [[paper](https://doi.org/10.1016/j.sna.2026.118150)]
- [2026] **Bioinspired perception: Advancements for underwater robots** *Ocean Engineering* [[paper](https://doi.org/10.1016/j.oceaneng.2026.125943)]
- [2026] **Triboelectric Tactile Sensors for Intelligent Systems** *SmartSys* [[paper](https://doi.org/10.1002/sys3.70023)]
- [2026] **Strain-localized luminescent e-skin for high-resolution pressure mapping and visual force feedback** *Nature Communications* [[paper](https://doi.org/10.1038/s41467-026-73073-5)]
- [2026] **3D-printed coaxial intelligent fibers with multimodal sensing capabilities for e-skin** *Chemical Engineering Journal* [[paper](https://doi.org/10.1016/j.cej.2026.176102)]
- [2026] **An Intrinsically Multimodal Self‐Powered Sensor Enhanced by Microstructured Powder Layer for AI‐Enabled Tactile Perception** *Interdisciplinary materials* [[paper](https://doi.org/10.1002/idm2.70045)]
- [2026] **Recent progresses on multifunctional tactile sensors for electronic skins and human-machine interaction applications** *Sensors and Actuators Reports* [[paper](https://doi.org/10.1016/j.snr.2026.100459)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **TouchReal: an online neuromorphic tactile framework for biomimetic afferent spike generation based on TouchSim** *Neuromorphic Computing and Engineering* [[paper](https://doi.org/10.1088/2634-4386/ae98b0)]
- [2026] **Multimodal Flexible Sensors Based on Porous Laser-Induced Graphene with Tunable Thermal Therapy and Haptic Perception** *ACS Applied Electronic Materials* [[paper](https://doi.org/10.1021/acsaelm.6c00853)]
- [2026] **High-resolution flexible tactile sensors** *Soft Science* [[paper](https://doi.org/10.20517/ss.2026.77)]
- [2026] **A Review of Intelligent Identification Technologies for the Collection of Tree-Derived Bio-Based Polymer Materials: Multimodal Perception and Machine Learning Methods** *Forests* [[paper](https://doi.org/10.3390/f17060727)]
- [2026] **Multidimensional Parameter Monitoring and Cross-Sensitivity Decoupling in Force-Sensing Optical Fibers: Mechanisms, Algorithms, and Experimental Validation** *Journal of engineering system.* [[paper](https://doi.org/10.62517/jes.202602226)]
- [2026] **Robotic Tactile Sensing for Early Detection of Frost-Damaged Citrus Fruits with Pressure–Vibration Multimodal Fusion** *Foods* [[paper](https://doi.org/10.3390/foods15091597)]
- [2026] **Flexible tactile sensors toward intelligent perception: Mechanisms, architectures and functional applications** *Chemical Engineering Journal* [[paper](https://doi.org/10.1016/j.cej.2026.177827)]
- [2026] **Tabero: Learning Gentle Manipulation with Closed-Loop Force Feedback from Vision, Touch, and Language** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2605.27886)]
- [2026] **Tutkimus deformoituvien objektien robottimanipulaatiosta: Havaitseminen, mallintaminen, suunnittelu ohjaus** *Aaltodoc (Aalto University)* [[paper](https://aaltodoc.aalto.fi/handle/123456789/144904)]
- [2026] **Manufacturing, Sensing, and Applications of Data Gloves: A Review** *IEEE Sensors Journal* [[paper](https://doi.org/10.1109/jsen.2026.3681433)]
- [2026] **FG-CLTP: Fine-Grained Contrastive Language Tactile Pretraining for Robotic Manipulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.10871)]
- [2026] **3DA-VTG: An Explicitly Aligned Visuo-Tactile Grasp Dataset and Dual-Branch Fusion Method for Robotic Stable Grasp** *Chinese Journal of Mechanical Engineering* [[paper](https://doi.org/10.1016/j.cjme.2026.100283)]
- [2026] **A Multimodal Sensor-Vision Fusion Dataset for Robotic Task Classification and Behavior Analysis in Industrial Environments** *International Multidisciplinary Knowledge Exchange Journal* [[paper](https://doi.org/10.65282/imke.vol.1.issue.02.038)]
- [2026] **Synergy-Driven Flexible Fragile Object Slip Detection Enhanced by Visuo-Tactile Abstract Representation Fusion** *IEEE Sensors Journal* [[paper](https://doi.org/10.1109/jsen.2026.3672447)]
- [2026] **TactEx: An Explainable Multimodal Robotic Interaction Framework for Human-Like Touch and Hardness Estimation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2602.18967)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Learning Physical Interaction: A Survey of Tactile- and Force-aware Robot Learning** [[paper](https://arxiv.org/abs/2608.07558)]
- [2026] **NestDex: Nested Policy Learning with Copilot Assisted Teleoperation for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2608.13362)]
- [2026] **AdaDexGrasp: Adaptive Dexterous Grasping via 3D Visuo-Tactile Representation Fusion** [[paper](https://arxiv.org/abs/2608.07600)]
- [2026] **Transcutaneous Spinal Cord Stimulation Disrupts Conscious Ankle Proprioception and Produces a More Constrained Locomotor Pattern in Unimpaired Adults** [[paper](https://arxiv.org/abs/2608.05635)]
- [2026] **ReTouch: Empowering Contact-Rich Dexterous Manipulation with Online-Refined Tactile Prediction** [[paper](https://arxiv.org/abs/2608.01824)]
- [2026] **Intrinsic Environmental Referencing in Coaxial Nanofiber Yarns Enables Humidity‐Robust Triboelectric Tactile Recognition** *Advanced Functional Materials* [[paper](https://doi.org/10.1002/adfm.77610)]
- [2026] **Imagining the Sense of Touch: Touch-Informed Manipulation via Imagined Tactile Representations** [[paper](https://arxiv.org/abs/2607.01684)]
- [2026] **A Model-Based Decoupling Strategy for Proprioception and Contact Sensing in an Architected Soft Manipulator** [[paper](https://arxiv.org/abs/2607.15582)]
- [2026] **TAC-LOCO: Unified Whole-Body Control for Quadrupedal TACtile-Informed LOCO-Manipulation** [[paper](https://arxiv.org/abs/2607.10132)]
- [2026] **τ: Learning Touch-Augmented Vision-Language-Action Models from Future Visual Supervision** [[paper](https://arxiv.org/abs/2607.24485)]
- [2026] **SoftVTBench: A Safety-Aware Visuo-Tactile Benchmark for Physically Constrained Robotic Manipulation of Deformable Objects** [[paper](https://arxiv.org/abs/2607.04234)]
- [2026] **Scalable Open-Source Visuotactile Sensor for 6-Axis Contact Wrench Estimation in Tensegrity Robots** [[paper](https://arxiv.org/abs/2607.15633)]
- [2026] **Representation-Aligned Tactile Grounding for Contact-Rich Robotic Manipulation** [[paper](https://arxiv.org/abs/2607.14609)]
- [2026] **FELT: Generating Tactile Signals from Vision for Visuo-Tactile Manipulation** [[paper](https://arxiv.org/abs/2607.20683)]
- [2026] **Human-Centric Transferable Tactile Pre-Training for Dexterous Robotic Manipulation** [[paper](https://arxiv.org/abs/2607.01067)]
- [2026] **VT-WAM: Visual-Tactile World Action Model for Contact-Rich Manipulation** [[paper](https://arxiv.org/abs/2607.02503)]
- [2026] **TacWAM: Anchor-Guided World Action Model with Mechanics-Aware Tactile Prediction** [[paper](https://arxiv.org/abs/2607.28391)]
- [2026] **Self‐Driven Hybrid Piezomagnetic–Iontronic Mechanoreceptors for Bimodal SA/RA Perception and Tactile Synthesis** *Small* [[paper](https://doi.org/10.1002/smll.74799)]
- [2026] **Bioinspired Rheological Sensing for Robotic Liquid Identification in Sealed Containers via Ultrafast Incipient Slip Detection** *Advanced Materials* [[paper](https://doi.org/10.1002/adma.73955)]
- [2026] **Pressure-Dependent Facial Expression Control Using Calibrated Force-Sensitive Sensors** *Hardware* [[paper](https://doi.org/10.3390/hardware4030013)]
- [2026] **Integrating Structured Knowledge for State and Geometry Estimation** *KiltHub Repository* [[paper](https://doi.org/10.1184/r1/33063812.v1)]
- [2026] **NoContactNoWorries: Estimating Contact through Vision and Proprioception for In-Hand Dexterous Manipulation** [[paper](https://arxiv.org/abs/2606.24450)]
- [2026] **Geometric Reconstruction of Extrinsic Contact Trajectories using Tactile Sensing and Proprioception for Tool Manipulation** [[paper](https://arxiv.org/abs/2606.22251)]
- [2026] **Tactile Genesis: Exploring Tactile Sensors at Scale for Learning Dexterous Tasks** [[paper](https://arxiv.org/abs/2606.22332)]
- [2026] **DexFuture: Hierarchical Future-State Visuomotor Targeting for Bimanual Dexterous Tool Use** [[paper](https://arxiv.org/abs/2606.05699)]
- [2026] **VibeAct: Vibration to Actions for Contact-Rich Reactive Robot Dexterity** [[paper](https://arxiv.org/abs/2606.27344)]
- [2026] **CT-VAM: A Cerebello-Thalamic-Inspired Vision-Action Model for Efficient Visuomotor Control** [[paper](https://arxiv.org/abs/2606.09572)]
- [2026] **A Human-Inspired Thumb-Index Robotic Hand with Strain Gauges Embedded in Soft Joints** [[paper](https://arxiv.org/abs/2606.21245)]
- [2026] **HT-Bench: Benchmarking and Learning Dexterous Full-Hand Tactile Representations with Egocentric Vision** [[paper](https://arxiv.org/abs/2606.19161)]
- [2026] **TacForeSight: Force-Guided Tactile World Model for Contact-Rich Manipulation** [[paper](https://arxiv.org/abs/2606.11184)]
- [2026] **Multi-Resolution Tactile Imitation Learning for Contact-Rich Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.06281)]
- [2026] **AetheRock: An Arm-Worn Robot Teaching System for Force-Guided Vision-Tactile Learning** [[paper](https://arxiv.org/abs/2606.09777)]
- [2026] **Heterogeneous Tactile Transformer** [[paper](https://arxiv.org/abs/2606.29948)]
- [2026] **UniTacVLA: Unified Tactile Understanding and Prediction in Vision Language Action Models** [[paper](https://arxiv.org/abs/2606.31723)]
- [2026] **FTP-1: A Generalist Foundation Tactile Policy Across Tactile Sensors for Contact-Rich Manipulation** [[paper](https://arxiv.org/abs/2606.13102)]
- [2026] **UniTac: A Unified Multimodal Model for Cross-Sensor Tactile Understanding and Generation** [[paper](https://arxiv.org/abs/2606.31451)]
- [2026] **Tactile sensing for material identification in robotics: a review of piezoelectric, triboelectric and multimodal approaches** [[paper](https://doi.org/10.7148/2026-0133)]
- [2026] **TouchWGNN: spatio-temporal tactile perception for multimodal dexterous manipulation** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1791424)]
- [2026] **Special Issue on Tactile and Proximity Sensing** *Journal of Robotics and Mechatronics* [[paper](https://doi.org/10.20965/jrm.2026.p0681)]
- [2026] **Haptics in Robotics: A Systematic Literature Review** *Studies in health technology and informatics* [[paper](https://doi.org/10.3233/shti260905)]
- [2026] **Tactile-based Multimodal Fusion in Embodied Intelligence: A Survey of Vision, Language, and Contact-Driven Paradigms** [[paper](https://arxiv.org/abs/2605.17336)]
- [2026] **roto 2.0: The Robot Tactile Olympiad** [[paper](https://arxiv.org/abs/2605.21429)]
- [2026] **Learning Robust Dexterous In-Hand Manipulation from Joint Sensors with Proprioceptive Transformer** [[paper](https://arxiv.org/abs/2605.21330)]
- [2026] **ShapeGrasp: Simultaneous Visuo-Haptic Shape Completion and Grasping for Improved Robot Manipulation** [[paper](https://arxiv.org/abs/2605.02347)]
- [2026] **ARISTO Hand: Sensing-Driven Distal Hyperextension for Fine-Grained Manipulation** [[paper](https://arxiv.org/abs/2605.30508)]
- [2026] **TacO: Benchmarking Tactile Sensors for Object Manipulation** [[paper](https://arxiv.org/abs/2605.21976)]
- [2026] **Speckle Skin‐Based Multimodal Tactile Perception for Fine Robotic Manipulation** *Advanced Intelligent Systems* [[paper](https://doi.org/10.1002/aisy.70420)]
- [2026] **Multimodal Autonomous Navigation by Fusing Visual and Tactile Perception for Deformable Obstacle Traversal** *Academic Journal of Emerging Technologies* [[paper](https://doi.org/10.63313/ajet.9056)]
- [2026] **A review of adaptive intelligence in tactile sensing robotic hands for human centered dexterous control** *Discover Mechanical Engineering* [[paper](https://doi.org/10.1007/s44245-026-00275-y)]
- [2026] **Multimodal Vision-Haptic Fusion and Bio-Haptic Intelligence for AI-Driven Surgical Robotics** *Advances in computational intelligence and robotics book series* [[paper](https://doi.org/10.4018/979-8-2600-0358-9.ch005)]
- [2026] **Thin and soft optical tactile sensor for highly sensitive object perception** *Optics Express* [[paper](https://doi.org/10.1364/oe.592013)]
- [2026] **Neuromorphic AI-Based e-Skin for Emotion-Sensitive Humanoid Robots** [[paper](https://doi.org/10.3390/engproc2026124114)]
- [2026] **AI-Driven Bio-Haptic Feedback Architectures for Semi-Autonomous Surgical Robotic Systems** *Advances in computational intelligence and robotics book series* [[paper](https://doi.org/10.4018/979-8-2600-0358-9.ch007)]
- [2026] **Smart Gripper with Triboelectric Sensors and Data-driven Machine Learning for Object Classification** *Nazarbayev University Repository (Nazarbayev University)* [[paper](https://nur.nu.edu.kz/handle/123456789/18910)]
- [2026] **A Biomimetic Palpation Platform for the Quantitative and Non‐Invasive Assessment of Tissue Compliance** *Advanced Healthcare Materials* [[paper](https://doi.org/10.1002/adhm.71212)]
- [2026] **Learning Tactile-Aware Quadrupedal Loco-Manipulation Policies** [[paper](https://arxiv.org/abs/2604.27224)]
- [2026] **OmniUMI: Towards Physically Grounded Robot Learning via Human-Aligned Multimodal Interaction** [[paper](https://arxiv.org/abs/2604.10647)]
- [2026] **Learning Versatile Humanoid Manipulation with Touch Dreaming** [[paper](https://arxiv.org/abs/2604.13015)]
- [2026] **FingerViP: Learning Real-World Dexterous Manipulation with Fingertip Visual Perception** [[paper](https://arxiv.org/abs/2604.21331)]
- [2026] **Physically Grounded 3D Generative Reconstruction under Hand Occlusion using Proprioception and Multi-Contact Touch** [[paper](https://arxiv.org/abs/2604.09100)]
- [2026] **Learning Structured Robot Policies from Vision-Language Models via Synthetic Neuro-Symbolic Supervision** [[paper](https://arxiv.org/abs/2604.02812)]
- [2026] **Multimodal Electronic Skin Integrating Discrete Wavelet Transform and Deep Learning for Accurate Tactile Perception** *Advanced Functional Materials* [[paper](https://doi.org/10.1002/adfm.75219)]
- [2026] **Multimodal Haptic Object Recognition: Can Kinesthetic Inference Compensate for the Lack of Tactile Sensing Resolution?** *IEEE Sensors Journal* [[paper](https://doi.org/10.1109/jsen.2026.3684076)]
- [2026] **Robust bionic distributed multimodal flexible sensor for extreme-condition sensing and intelligent operation** *Communications Engineering* [[paper](https://doi.org/10.1038/s44172-026-00653-0)]
- [2026] **PTLD: Sim-to-real Privileged Tactile Latent Distillation for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2603.04531)]
- [2026] **ReTac-ACT: A State-Gated Vision-Tactile Fusion Transformer for Precision Assembly** [[paper](https://arxiv.org/abs/2603.09565)]
- [2026] **Cable-driven Continuum Robotics: Proprioception via Proximal-integrated Force Sensing** [[paper](https://arxiv.org/abs/2603.07426)]
- [2026] **Foundational World Models Accurately Detect Bimanual Manipulator Failures** [[paper](https://arxiv.org/abs/2603.06987)]
- [2026] **Active Stereo-Camera Outperforms Multi-Sensor Setup in ACT Imitation Learning for Humanoid Manipulation** [[paper](https://arxiv.org/abs/2603.28422)]
- [2026] **MuxGel: Simultaneous Dual-Modal Visuo-Tactile Sensing via Spatially Multiplexing and Deep Reconstruction** [[paper](https://arxiv.org/abs/2603.09761)]
- [2026] **FutureVLA: Joint Visuomotor Prediction for Vision-Language-Action Model** [[paper](https://arxiv.org/abs/2603.10712)]
- [2026] **CHOP: Counterfactual Human Preference Labels Improve Obstacle Avoidance in Visuomotor Navigation Policies** [[paper](https://arxiv.org/abs/2603.02004)]
- [2026] **CLTP: Contrastive Language-Tactile Pre-training for 3D contact geometry understanding** *Biomimetic Intelligence and Robotics* [[paper](https://doi.org/10.1016/j.birob.2026.100324)]
- [2026] **Localization Based Grasping for Robotic Grippers** *Academic Journal of Science and Technology* [[paper](https://doi.org/10.54097/948twa81)]
- [2026] **Edge-intelligent bimodal iontronic skin for human−robot collaboration** *National Science Review* [[paper](https://doi.org/10.1093/nsr/nwag194)]
- [2026] **High-Precision 3-D Reconstruction of a Vision-Based Tactile Sensor Using a Dense Color Marker Array** *IEEE Sensors Journal* [[paper](https://doi.org/10.1109/jsen.2026.3675787)]
- [2026] **DECO: Decoupled Multimodal Diffusion Transformer for Bimanual Dexterous Manipulation with a Plugin Tactile Adapter** [[paper](https://arxiv.org/abs/2602.05513)]
- [2026] **Why Look at It at All?: Vision-Free Multifingered Blind Grasping Using Uniaxial Fingertip Force Sensing** [[paper](https://arxiv.org/abs/2602.07326)]
- [2026] **When would Vision-Proprioception Policies Fail in Robotic Manipulation?** [[paper](https://arxiv.org/abs/2602.12032)]
- [2026] **A Perspective on Open Challenges in Deformable Object Manipulation** [[paper](https://arxiv.org/abs/2602.22998)]
- [2026] **UniVTAC: A Unified Simulation Platform for Visuo-Tactile Manipulation Data Generation, Learning, and Benchmarking** [[paper](https://arxiv.org/abs/2602.10093)]
- [2026] **AnyTouch 2: General Optical Tactile Representation Learning For Dynamic Tactile Perception** [[paper](https://arxiv.org/abs/2602.09617)]
- [2026] **Think Proprioceptively: State-Grounded Visual Token Selection for VLA Policies** [[paper](https://arxiv.org/abs/2602.06575)]
- [2026] **Mechanoreceptor-inspired multisensory fibers for artificial somatosensation** *npj Flexible Electronics* [[paper](https://doi.org/10.1038/s41528-026-00555-3)]
- [2026] **TouchGuide: Inference-Time Steering of Visuomotor Policies via Touch Guidance** [[paper](https://arxiv.org/abs/2601.20239)]
- [2026] **Test-Time Adaptation for Tactile-Vision-Language Models** [[paper](https://arxiv.org/abs/2602.15873)]
- [2026] **Tactile Memory with Soft Robot: Robust Object Insertion via Masked Encoding and Soft Wrist** [[paper](https://arxiv.org/abs/2601.19275)]
- [2026] **TaF-VLA: Tactile-Force Alignment in Vision-Language-Action Models for Force-aware Manipulation** [[paper](https://arxiv.org/abs/2601.20321)]

##### 2025

- [2025] **Simultaneous Tactile-Visual Perception for Learning Multimodal Robot Manipulation** [[paper](https://arxiv.org/abs/2512.09851)]
- [2025] **Residual Rotation Correction using Tactile Equivariance** [[paper](https://arxiv.org/abs/2511.07381)]
- [2025] **MILE: A Mechanically Isomorphic Hand Exoskeleton and Visuotactile Robotic Hand for Data Collection in Dexterous Manipulation** [[paper](https://arxiv.org/abs/2512.00324)]
- [2025] **Continuous Vision-Language-Action Co-Learning with Semantic-Physical Alignment for Behavioral Cloning** [[paper](https://arxiv.org/abs/2511.14396)]
- [2025] **SeFA-Policy: Fast and Accurate Visuomotor Policy Learning with Selective Flow Alignment** [[paper](https://arxiv.org/abs/2511.08583)]
- [2025] **Tactile Robotics: Past and Future** [[paper](https://arxiv.org/abs/2512.01106)]
- [2025] **Collaborative Representation Learning for Alignment of Tactile, Language, and Vision Modalities** [[paper](https://arxiv.org/abs/2511.11512)]
- [2025] **Enhancing Tactile-based Reinforcement Learning for Robotic Control** [[paper](https://arxiv.org/abs/2510.21609)]
- [2025] **Tailored robotic training improves hand function and proprioceptive processing in stroke survivors with proprioceptive deficits: A randomized controlled trial** [[paper](https://arxiv.org/abs/2511.00259)]
- [2025] **ViTacGen: Robotic Pushing with Vision-to-Touch Generation** [[paper](https://arxiv.org/abs/2510.14117)]
- [2025] **Factorizing Diffusion Policies for Observation Modality Prioritization** [[paper](https://arxiv.org/abs/2509.16830)]
- [2025] **exUMI: Extensible Robot Teaching System with Action-aware Task-agnostic Tactile Representation** [[paper](https://arxiv.org/abs/2509.14688)]
- [2025] **VGGT-DP: Generalizable Robot Control via Vision Foundation Models** [[paper](https://arxiv.org/abs/2509.18778)]
- [2025] **Do You Need Proprioceptive States in Visuomotor Policies?** [[paper](https://arxiv.org/abs/2509.18644)]
- [2025] **Underactuated Robotic Hand with Grasp State Estimation Using Tendon-Based Proprioception** [[paper](https://arxiv.org/abs/2509.12969)]
- [2025] **Grasp Like Humans: Learning Generalizable Multi-Fingered Grasping from Human Proprioceptive Sensorimotor Integration** [[paper](https://arxiv.org/abs/2509.08354)]
- [2025] **ManiFlow: A General Robot Manipulation Policy via Consistency Flow Training** [[paper](https://arxiv.org/abs/2509.01819)]
- [2025] **DEXOP: A Device for Robotic Transfer of Dexterous Human Manipulation** [[paper](https://arxiv.org/abs/2509.04441)]
- [2025] **VisualMimic: Visual Humanoid Loco-Manipulation via Motion Tracking and Generation** [[paper](https://arxiv.org/abs/2509.20322)]
- [2025] **Human-Inspired Soft Anthropomorphic Hand System for Neuromorphic Object and Pose Recognition Using Multimodal Signals** [[paper](https://arxiv.org/abs/2509.02275)]
- [2025] **PneuGelSight: Soft Robotic Vision-Based Proprioception and Tactile Sensing** [[paper](https://arxiv.org/abs/2508.18443)]
- [2025] **Gentle Object Retraction in Dense Clutter Using Multimodal Force Sensing and Imitation Learning** [[paper](https://arxiv.org/abs/2508.19476)]

[⬆ Back to top](#paper-list)

#### Application

##### 2026

- [2026] **A Haptic Robot Finger Designed for Guqin Instrument Playing** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2608.07002)]
- [2026] **Advances in material design and applications of electronic skins: From human body to embodied intelligent robots** *Progress in Materials Science* [[paper](https://doi.org/10.1016/j.pmatsci.2026.101786)]
- [2026] **A Folded, Structure‐Integrated Bimodal Sensor Enabling Non‐Contact and Tactile Perception for Intelligent Robots** *Advanced Science* [[paper](https://doi.org/10.1002/advs.75868)]
- [2026] **Applications and Challenges of Tactile Sensing Technology in Robotic Grasping** *Applied and Computational Engineering* [[paper](https://doi.org/10.54254/2755-2721/2026.gu33613)]
- [2026] **Multimodal Haptic Perception Through Synergistic Nanocomposite Sensor Arrays** *Advanced Materials Technologies* [[paper](https://doi.org/10.1002/admt.202600010)]
- [2026] **From Proximity toContact Perception of PiezoelectricExtended-Gate Amorphous Oxide Thin Film Transistors** *Figshare* [[paper](https://figshare.com/articles/journal_contribution/From_Proximity_to_Contact_Perception_of_Piezoelectric_Extended-Gate_Amorphous_Oxide_Thin_Film_Transistors/32127269)]
- [2026] **From Proximity to Contact Perception of Piezoelectric Extended-Gate Amorphous Oxide Thin Film Transistors** *ACS Applied Materials & Interfaces* [[paper](https://doi.org/10.1021/acsami.6c00084)]

[⬆ Back to top](#paper-list)

#### Development

##### 2026

- [2026] **Synergistic Integration of Artificial Merkel Disc and Meissner Corpuscle via Dermal Papillary Structures for Mechanically Filtered Multimodal Tactile Sensing** *Advanced Science* [[paper](https://doi.org/10.1002/advs.76069)]
- [2026] **Neuro-inspired tactile system for robotic embodied perception** *Chemical Engineering Journal* [[paper](https://doi.org/10.1016/j.cej.2026.174954)]

[⬆ Back to top](#paper-list)

#### Systems & Technology

##### 2026

- [2026] **Aligned electrospun nanofiber-engineered triboelectric interface for non-acoustic human-robot communication and material-adaptive manipulation** *Composites Part B Engineering* [[paper](https://doi.org/10.1016/j.compositesb.2026.114060)]
- [2026] **Bionic Tursiops Truncatus-inspired dual-mode sensor for proximity sensing and high-resolution tactile perception** *Chemical Engineering Journal* [[paper](https://doi.org/10.1016/j.cej.2026.177786)]
- [2026] **A liquid metal film-based passive tactile sensor for robotic perception** *Science China Technological Sciences* [[paper](https://doi.org/10.1007/s11431-025-3177-6)]
- [2026] **Integrated in-memory and near-memory sensor for bionic robot perception** *Materials Today* [[paper](https://doi.org/10.1016/j.mattod.2026.103345)]

[⬆ Back to top](#paper-list)

#### Evaluation & Benchmarks

##### 2026

- [2026] **A single-element multimodal tactile interface with geometric signal encoding for robust robotic material and slip intelligence** *Nano Energy* [[paper](https://doi.org/10.1016/j.nanoen.2026.112076)]

[⬆ Back to top](#paper-list)

### Planning & Control

#### Theory

##### 2026

- [2026] **INVERSE KINEMATICS AND TRAJECTORY PLANNING OF ROBOTIC SYSTEMS USING REINFORCEMENT LEARNING TECHNIQUES** *Purdue* [[paper](https://doi.org/10.25394/pgs.33183827)]
- [2026] **GASP: GPU-Accelerated Safe Planner for Real-Time Collision-Aware Motion Generation with Latent Trajectory Sampling** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2608.04612)]
- [2026] **ACO-optimized S-curve trajectory and HTSMC-PPC-ESO control for robust sloshing suppression in liquid transportation using a biglide parallel robot** *European Journal of Control* [[paper](https://doi.org/10.1016/j.ejcon.2026.101555)]
- [2026] **Distributed Motion Planning with Safety Guarantees for Self-Reconfiguring Robotic Boats** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.20352)]
- [2026] **Method for Motion Route Planning of a Ground Robotic System for Substation Equipment Condition Monitoring and Technical Diagnostics** *Intellekt Sist Proizv* [[paper](https://doi.org/10.22213/2410-9304-2026-2-90-99)]
- [2026] **Asymmetric S-Curve Velocity Control for Smooth Obstacle-Avoidance Trajectory Execution in Stepper-Motor-Driven Selective Compliance Assembly Robot Arms** *Machines* [[paper](https://doi.org/10.3390/machines14070764)]
- [2026] **Robust model predictive control of robots in confined spaces** *FreiDok plus (Universitätsbibliothek Freiburg)* [[paper](https://freidok.uni-freiburg.de/data/284779)]
- [2026] **Control of a Polishing pResearch on Trajectory Planning and Motion Parallel Robot for the Aspheric Optical Mirror** *Mechanisms and machine science* [[paper](https://doi.org/10.1007/978-981-95-7904-4_72)]
- [2026] **Nonlinear kinematic modeling and remote center of motion optimization of flexible surgical robots** *Nonlinear Dynamics* [[paper](https://doi.org/10.1007/s11071-026-12734-y)]
- [2026] **Manipulator Hugging Motion Control Based on Optimal Human Tactile Force** *International Journal of Social Robotics* [[paper](https://doi.org/10.1007/s12369-026-01413-y)]
- [2026] **Motion trajectory planning for industrial robots based on BAS‑IPSO** *DOAJ (DOAJ: Directory of Open Access Journals)* [[paper](https://doaj.org/article/60ab6477058145bdb750d24aaf79a8c2)]
- [2026] **Biomimetic Trajectory Planning and Implementation of Quadruped Robots Based on Biological Motion Characteristics** *DOAJ (DOAJ: Directory of Open Access Journals)* [[paper](https://doaj.org/article/3aca939e9cf1478f8adb5324a0d51465)]
- [2026] **General introduction to recent advancements in path and trajectory planning for robots and autonomous machines** *International Journal of Advanced Robotic Systems* [[paper](https://doi.org/10.1177/17298806261446021)]
- [2026] **Fuzzy-DDPG: Integrating fuzzy logic with continuous deep reinforcement learning for mobile robot motion planning** *Fuzzy Sets and Systems* [[paper](https://doi.org/10.1016/j.fss.2026.109967)]
- [2026] **Graph-search planning and dual-target Cartesian control for cross-plane dual-arm climbing of a robotic astronaut** *Aerospace Science and Technology* [[paper](https://doi.org/10.1016/j.ast.2026.112708)]
- [2026] **Calculation and Analysis of the Spatial Motion Trajectory of the Grasping Mechanism of a Pipe Handling Manipulator for Coal Mines** *Journal of Engineering Research and Reports* [[paper](https://doi.org/10.9734/jerr/2026/v28i51891)]
- [2026] **A dynamic control strategy for thermal management of depositions in robotic wire-arc additive manufacturing** *Journal of Manufacturing Processes* [[paper](https://doi.org/10.1016/j.jmapro.2026.05.048)]
- [2026] **A Unified Analytical Framework for Dynamically Stable and Energy-Efficient Motion Planning in Humanoid Robots** *Textile & Leather Review* [[paper](https://doi.org/10.31881/tlr.2026.2146)]
- [2026] **Integrating Adaptive Constraints with an Enhanced Metaheuristic for Zero-Latency Trajectory Planning in Robotic Manufacturing Processes** *Processes* [[paper](https://doi.org/10.3390/pr14081282)]
- [2026] **BeetleBrush: A bio-inspired and LLM-RAG-augmented framework for trajectory planning in robotic drawing tasks** *Expert Systems with Applications* [[paper](https://doi.org/10.1016/j.eswa.2026.132474)]
- [2026] **Path planning for fracture reduction robots incorporating physiological tissue response and safety-oriented optimization** *International Journal of Computer Assisted Radiology and Surgery* [[paper](https://doi.org/10.1007/s11548-026-03607-1)]
- [2026] **Perceptive Whole-body Motion Planning for Multi-legged Robots in Unstructured Confined Environments** *Open MIND* [[paper](https://hdl.handle.net/1880/124702)]
- [2026] **Smooth Feedback Motion Planning with Reduced Curvature** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.01614)]
- [2026] **Energy and Efficiency Optimization of Six-Axis Robotic Arms Using Taguchi Coupled Principal Component Analysis** *Arabian Journal for Science and Engineering* [[paper](https://doi.org/10.1007/s13369-026-11307-w)]
- [2026] **Path planning for volumetric flask grasping based on visual guidance and multi-constraint optimization** *PLoS ONE* [[paper](https://doi.org/10.1371/journal.pone.0347043)]
- [2026] **Optimal motion planning and decoupled control for autonomous mobile robots based on minimum energy consumption** *Expert Systems with Applications* [[paper](https://doi.org/10.1016/j.eswa.2026.131995)]
- [2026] **Towards the development of a robotic spraying arm: AI-based weed detection and path planning strategies** *Robotics and Autonomous Systems* [[paper](https://doi.org/10.1016/j.robot.2026.105443)]
- [2026] **Bio-Inspired Metaheuristics for Time-Optimal Trajectory Planning in Cooperative Dual-Arm Bimanipulation** *Biomimetics* [[paper](https://doi.org/10.3390/biomimetics11030173)]
- [2026] **A Riemannian take on distance fields and geodesic flows in robotics** *The International Journal of Robotics Research* [[paper](https://doi.org/10.1177/02783649261420233)]
- [2026] **ECA-RRT*: A robotic arm path planning algorithm based on environment complexity adaptive heuristic strategy** *Journal of Computational Science* [[paper](https://doi.org/10.1016/j.jocs.2026.102820)]
- [2026] **Quantum Computing for Robotics: Algorithms, Optimization, and Future Systems.** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.18759895)]
- [2026] **RRT$^η$: Sampling-based Motion Planning and Control from STL Specifications using Arithmetic-Geometric Mean Robustness** *Open MIND* [[paper](https://arxiv.org/abs/2602.16825)]
- [2026] **A Bio-Inspired Fluid Dynamics Approach for Unified and Efficient Path Planning and Control** *Actuators* [[paper](https://doi.org/10.3390/act15030133)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **Real-Time Coverage Path Planning for Fixed-Wing Aerial Robots Using Partial Gradient-Based MPC and Augmented Dubins Trajectories** *Aerospace* [[paper](https://doi.org/10.3390/aerospace13080713)]
- [2026] **Learning-Augmented Motion Planning and Control for Legged and Hybrid Locomotion** *CINECA IRIS Institutial Research Information System (University of Genoa)* [[paper](https://hdl.handle.net/11567/1310018)]
- [2026] **Experimental investigation of automatic operation trajectory planning and tracking of unmanned excavators** *Transactions of the Institute of Measurement and Control* [[paper](https://doi.org/10.1177/01423312261463306)]
- [2026] **PHYSICS-INFORMED LEARNING FOR MOTION PLANNING** *Purdue* [[paper](https://doi.org/10.25394/pgs.32104864.v1)]
- [2026] **Cooperative Interaction and Manipulation in Human-Robot and Multi-Robot Systems** *CINECA IRIS Institutial Research Information System (University of Genoa)* [[paper](https://hdl.handle.net/11567/1294736)]
- [2026] **MULTI-AGENT COOPERATIVE CONTROL ARCHITECTURE FOR AUTONOMOUS INDUSTRIAL ROBOTS IN SMART MANUFACTURING ENVIRONMENTS** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.18863513)]
- [2026] **Advancements and prospects in key technologies for robotic pollination in greenhouse pepper breeding: a review** *Frontiers in Plant Science* [[paper](https://doi.org/10.3389/fpls.2026.1778541)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Real-time Whole-Body Motion Planning for Mobile Manipulators Carrying Arbitrarily Shaped Payloads via Kinematically-Coupled SVSDF** [[paper](https://arxiv.org/abs/2608.07005)]
- [2026] **Risk-Aware Kinodynamic Motion Planning Under Uncertainty For Safe Navigation on Planetary Environments** [[paper](https://arxiv.org/abs/2608.11175)]
- [2026] **ContactGuard: Pre-Contact Execution Monitoring with Action-Conditioned Latent World Models** [[paper](https://arxiv.org/abs/2608.13438)]
- [2026] **Deliberate Practice: Learning Robot Skills under a Budget** [[paper](https://arxiv.org/abs/2608.13415)]
- [2026] **A Review of Trajectory Planning and Path Tracking Methods for Mobile Robots** *Applied and Computational Engineering* [[paper](https://doi.org/10.54254/2755-2721/2026.35762)]
- [2026] **Moving horizon-based online collaboration of motion planning and robust control for time-varying nonlinear uncertain system in unstructured environment** *Chinese Journal of Aeronautics* [[paper](https://doi.org/10.1016/j.cja.2026.104409)]
- [2026] **Multimodal Machine Learning Models Using Zero-Shot Learning to Control Robots** [[paper](https://doi.org/10.3390/engproc2026150104)]
- [2026] **Motion Planning for Mobile Manipulators Navigating Doorways via Model Predictive Control** [[paper](https://arxiv.org/abs/2608.00206)]
- [2026] **Model Predictive Planner for UAV Navigation in Non-Convex Air Corridors** [[paper](https://arxiv.org/abs/2607.24369)]
- [2026] **NeHMO: Neural Hamilton-Jacobi Reachability Learning for Decentralized Safe Multi-Arm Motion Planning** [[paper](https://arxiv.org/abs/2607.00326)]
- [2026] **Ace! Motion Planning of Professional-Level Table Tennis Serves with a Robot Arm** [[paper](https://arxiv.org/abs/2607.06989)]
- [2026] **Search-Based Spatiotemporal and Multi-Robot Motion Planning on Graphs of Space-Time Convex Sets** [[paper](https://arxiv.org/abs/2607.00444)]
- [2026] **Task-Space Constrained Stochastic Trajectory Optimization for Time-Optimal Forestry Crane Motion Planning** [[paper](https://arxiv.org/abs/2607.17818)]
- [2026] **A Task-Space Receding Horizon Controller for Fast Collision Avoidance** [[paper](https://arxiv.org/abs/2607.15733)]
- [2026] **Safe Overtaking for Autonomous Racing Using Hierarchical Optimization and Learning-Based Control** [[paper](https://arxiv.org/abs/2607.13348)]
- [2026] **Motion Planning with Model-Based Diffusion via Constraint Optimization and Adaptive Scheduling** [[paper](https://arxiv.org/abs/2607.14455)]
- [2026] **Motion Generation With Environmental Constraints** [[paper](https://arxiv.org/abs/2607.25053)]
- [2026] **Catch, Throw, Repeat: Planning for Human-Robot Partner Juggling** [[paper](https://arxiv.org/abs/2607.15129)]
- [2026] **Multi-Rate Nonlinear Model Predictive Control for Wall-Supported Bipedal Locomotion of Quadrupedal Robots** [[paper](https://arxiv.org/abs/2607.01574)]
- [2026] **Disturbance-Aware Flight for Aerial Robots in Narrow Space** [[paper](https://arxiv.org/abs/2607.17476)]
- [2026] **HumAIN: Human-Aware Implicit Social Robot Navigation** [[paper](https://arxiv.org/abs/2607.07357)]
- [2026] **Affordance-Based Manipulation Planning with Text Goals and Sim-to-Real Generalisation via Real-to-Sim Image Conversion** [[paper](https://arxiv.org/abs/2607.11004)]
- [2026] **From Passive Video to Editable Experience: Physically Grounded Experience Synthesis for Embodied Intelligence** [[paper](https://arxiv.org/abs/2607.26903)]
- [2026] **ACME: A Multi-Cultural, Multi-Embodiment Social-Navigation Dataset** [[paper](https://arxiv.org/abs/2607.21964)]
- [2026] **Robotic arm trajectory planning based on a multi-strategy improved seagull optimization algorithm** *The Journal of Supercomputing* [[paper](https://doi.org/10.1007/s11227-026-08730-z)]
- [2026] **A Bio-inspired Integrated Framework for Disturbance Rejection Whole-Body Control of Humanoid Robots** *Journal of Bionic Engineering* [[paper](https://doi.org/10.1007/s42235-026-00965-z)]
- [2026] **Pixels to Proofs: Probabilistically-Safe Latent World Model Control via Parallel Conformal Robust MPC** [[paper](https://arxiv.org/abs/2606.15594)]
- [2026] **Motion Planning in Dynamic Environments: A Survey from Classical to Modern Methods** [[paper](https://arxiv.org/abs/2606.02677)]
- [2026] **Short-Horizon Position Accuracy of Single-Track Models: Implications for Motion Planning of Autonomous Vehicles** [[paper](https://arxiv.org/abs/2606.14216)]
- [2026] **Scaling Nonlinear Optimization: Many Problems One GPU** [[paper](https://arxiv.org/abs/2606.26341)]
- [2026] **Learning Predictive Control with Deep Koopman Operators for Autonomous Vehicle Motion Planning** [[paper](https://arxiv.org/abs/2606.08136)]
- [2026] **Safe Polytope-in-Polytope Motion Planning and Control with Control Barrier Functions** [[paper](https://arxiv.org/abs/2606.09719)]
- [2026] **Temporal logics and formal synthesis for robot planning and control** [[paper](https://arxiv.org/abs/2606.21438)]
- [2026] **Event-Adaptive Motion Planning with Distilled Vision-Language Model in Safety-Critical Situations** [[paper](https://arxiv.org/abs/2606.25629)]
- [2026] **LieIPM: Lie Group Interior Point Method for Direct Trajectory Optimization of Rigid Bodies** [[paper](https://arxiv.org/abs/2606.10579)]
- [2026] **Semantic Constraint Synthesis for Adaptive Trajectory Optimization via Large Language Models** [[paper](https://arxiv.org/abs/2606.04123)]
- [2026] **DSIP: A Dynamic Coordination Planner for Signal-Free Intersections using Diffusion-Model-Based Multi-Agent Motion Planning** [[paper](https://arxiv.org/abs/2606.30694)]
- [2026] **ExoTraj: A General Lower-limb Exoskeleton Assistance Policy for Complex Environments** [[paper](https://arxiv.org/abs/2606.16876)]
- [2026] **Sensitivity Shaping for Latent Modeling** [[paper](https://arxiv.org/abs/2606.14585)]
- [2026] **EV-WM: Event-Verified World Models for Long-Horizon Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.13053)]
- [2026] **Human2Any: Human-to-Robot Transfer via Constraint-Aware Compositional Planning** [[paper](https://arxiv.org/abs/2606.28813)]
- [2026] **PO-PDDL: Learning Symbolic POMDPs from Visual Demonstrations for Robot Planning Under Uncertainty** [[paper](https://arxiv.org/abs/2606.15654)]
- [2026] **Grasp-Then-Plan with Failure Attribution: A Closed Two-Stage Framework for Precise and Generalizable Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.03385)]
- [2026] **Robustness of Robotic Manipulation: Foundations and Frontiers** [[paper](https://arxiv.org/abs/2606.31494)]
- [2026] **Motion Planning in Compressed Representation Spaces** [[paper](https://arxiv.org/abs/2606.30940)]
- [2026] **WatchAct: A Benchmark for Behavior-Grounded Robot Manipulation** [[paper](https://arxiv.org/abs/2606.26443)]
- [2026] **VLK: Learning Humanoid Loco-Manipulation from Synthetic Interactions in Reconstructed Scenes** [[paper](https://arxiv.org/abs/2606.30645)]
- [2026] **Safe Embodied AI for Long-horizon Tasks: A Cross-layer Analysis of Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.05660)]
- [2026] **JPPD: Joint Prediction_Planning Diffusion with Differentiable Safety Guidance for Dynamic Obstacle Avoidance in Intelligent Transportation Systems** [[paper](https://arxiv.org/abs/2606.20686)]
- [2026] **Unifying Object-Centric World Models and Diffusion Policy: A Hierarchical Framework for Multi-Stage Robotic Tasks** [[paper](https://arxiv.org/abs/2606.08775)]
- [2026] **Bounding Boxes as Goals: Language-Conditioned Grasping via Neuro-Symbolic Planning** [[paper](https://arxiv.org/abs/2606.12910)]
- [2026] **Embodied-BenchClaw: An Autonomous Multi-Agent System for Embodied Spatial Intelligence Benchmark Construction** [[paper](https://arxiv.org/abs/2606.11909)]
- [2026] **Dive into the Scene: Breaking the Perceptual Bottleneck in Vision-Language Decision Making via Focus Plan Generation** [[paper](https://arxiv.org/abs/2606.04046)]
- [2026] **SpaceVLN: A Zero-Shot Vision-and-Language Navigation Agent with Online Spatial Cognitive Memory and Reasoning** [[paper](https://arxiv.org/abs/2606.08992)]
- [2026] **THREAD: Trajectory Planning for Hybrid Rigid-Soft Manipulators with Environment-Aware Diffusion** [[paper](https://arxiv.org/abs/2606.21792)]
- [2026] **Foresight: Iterative Reasoning About Clues that Matter for Navigation** [[paper](https://arxiv.org/abs/2606.12550)]
- [2026] **TRAJECTORY OPTIMIZATION OF ROBOTS VIA MODEL PREDICTIVE CONTROL AND REINFORCEMENT LEARNING** *Tạp chí Khoa học Đại học Công Thương.* [[paper](https://doi.org/10.62985/j.huit_ojs.vol26.no2e.413)]
- [2026] **Vision-Guided Motion Planning for Autonomous Catch with a Robotic Arm** *DigitalCommons - CalPoly (California State Polytechnic University)* [[paper](https://digitalcommons.calpoly.edu/eesp/729)]
- [2026] **Optimization-Oriented Vision-Guided Robotic Grasping for Bolt Handling in Intelligent Manufacturing** *Mathematics* [[paper](https://doi.org/10.3390/math14122133)]
- [2026] **Application of hybrid artificial potential field method in local path planning of mobile robots** *Franklin Open* [[paper](https://doi.org/10.1016/j.fraope.2026.100694)]
- [2026] **An Improved A*-Based Path-Planning Framework for Facility Agricultural Robots** *Applied Sciences* [[paper](https://doi.org/10.3390/app16126138)]
- [2026] **Feedback Motion Planning for Stochastic Nonlinear Systems with Signal Temporal Logic Specifications** [[paper](https://arxiv.org/abs/2605.02361)]
- [2026] **IMPACT: An Implicit Active-Set Augmented Lagrangian for Fast Contact-Implicit Trajectory Optimization** [[paper](https://arxiv.org/abs/2605.09127)]
- [2026] **Probabilistic Recursively Feasible Motion Planning Under Uncertain Environments** [[paper](https://arxiv.org/abs/2605.19015)]
- [2026] **PISTO: Proximal Inference for Stochastic Trajectory Optimization** [[paper](https://arxiv.org/abs/2605.07215)]
- [2026] **Branch-Stochastic Model Predictive Control for Motion Planning under Multi-Modal Uncertainty with Scenario Clustering** [[paper](https://arxiv.org/abs/2605.22600)]
- [2026] **Parking Assistance for Trailer-Truck Transport Vehicles Using Sensor Fusion and Motion Planning** [[paper](https://arxiv.org/abs/2605.02716)]
- [2026] **TinySDP: Real Time Semidefinite Optimization for Certifiable and Agile Edge Robotics** [[paper](https://arxiv.org/abs/2605.13748)]
- [2026] **Optimizing Trajectory-Trees in Belief Space: An Application from Model Predictive Control to Task and Motion Planning** [[paper](https://arxiv.org/abs/2605.01860)]
- [2026] **Motion Planning for Autonomous Vehicles using Optimization over Graphs of Convex Sets** [[paper](https://arxiv.org/abs/2605.14199)]
- [2026] **The Open Motion Planning Library 2.0** [[paper](https://arxiv.org/abs/2605.29301)]
- [2026] **Graph Neural Planning and Predictive Control for Multi-Robot Communication-Constrained Unlabeled Motion Planning** [[paper](https://arxiv.org/abs/2605.19209)]
- [2026] **Constrained MPC-Based Motion Planning for Morphing Quadrotors in Ultra-Narrow Passages under Limited Perception** [[paper](https://arxiv.org/abs/2605.15999)]
- [2026] **Scout-Assisted Planning for Heterogeneous Robot Teams under Partially Known Environments** [[paper](https://arxiv.org/abs/2605.22693)]
- [2026] **Performance Comparison of Classical and Neural Sampling Algorithms for Robotic Navigation** [[paper](https://arxiv.org/abs/2605.25010)]
- [2026] **Not What You Asked For: Typographic Attacks in Household Robot Manipulation** [[paper](https://arxiv.org/abs/2605.18593)]
- [2026] **Visual Sculpting: Visually-Aligned Planning Representations for Long-Horizon Robot Clay Sculpting** [[paper](https://arxiv.org/abs/2605.17556)]
- [2026] **Neural Operators for Design-Space Surrogate Modeling of Tendon-Actuated Continuum Robots** [[paper](https://arxiv.org/abs/2605.19104)]
- [2026] **GSAM: A Generalizable and Safe Robotic Framework for Articulated Object Manipulation** [[paper](https://arxiv.org/abs/2605.30740)]
- [2026] **No Plan, Yet Human: A Reactive Robotics Model Predicts Human Planning Failures on a Clinical Task** [[paper](https://arxiv.org/abs/2605.16514)]
- [2026] **World-Ego Modeling for Long-Horizon Evolution in Hybrid Embodied Tasks** [[paper](https://arxiv.org/abs/2605.19957)]
- [2026] **Motion Planning of a Mobile Robot Using Model Predictive Control** *Nazarbayev University Repository (Nazarbayev University)* [[paper](https://nur.nu.edu.kz/handle/123456789/18979)]
- [2026] **Optimal control–based trajectory optimization for obstacle-avoiding robotic filament winding** *Transactions of the Institute of Measurement and Control* [[paper](https://doi.org/10.1177/01423312261447563)]
- [2026] **Time-energy optimal smooth trajectory planning for mobile robots** *Physica Scripta* [[paper](https://doi.org/10.1088/1402-4896/ae72d0)]
- [2026] **Path Optimization for 6-axis Robot Control Using Open Simulation-based Reinforcement Learning** *Journal of the Korean Society for Precision Engineering* [[paper](https://doi.org/10.7736/jkspe.026.00010)]
- [2026] **Emergency Stopping for Liquid-manipulating Robots** [[paper](https://arxiv.org/abs/2604.16667)]
- [2026] **Uncertainty Guided Exploratory Trajectory Optimization for Sampling-Based Model Predictive Control** [[paper](https://arxiv.org/abs/2604.12149)]
- [2026] **Dynamic Whole-Body Dancing with Humanoid Robots -- A Model-Based Control Approach** [[paper](https://arxiv.org/abs/2604.03999)]
- [2026] **Multi-Robot Motions in Milliseconds: Vector-Accelerated Primitives for Sampling-Based Planning** [[paper](https://arxiv.org/abs/2604.23960)]
- [2026] **Navigating the Clutter: Waypoint-Based Bi-Level Planning for Multi-Robot Systems** [[paper](https://arxiv.org/abs/2604.21138)]
- [2026] **Flow Motion Policy: Manipulator Motion Planning with Flow Matching Models** [[paper](https://arxiv.org/abs/2604.07084)]
- [2026] **NEAT-NC: NEAT guided Navigation Cells for Robot Path Planning** [[paper](https://arxiv.org/abs/2604.15076)]
- [2026] **Build on Priors: Vision--Language--Guided Neuro-Symbolic Imitation Learning for Data-Efficient Real-World Robot Manipulation** [[paper](https://arxiv.org/abs/2604.03759)]
- [2026] **AffordSim: A Scalable Data Generator and Benchmark for Affordance-Aware Robotic Manipulation** [[paper](https://arxiv.org/abs/2604.11674)]
- [2026] **Hippo: High-performance Interior-Point and Projection-based Solver for Generic Constrained Trajectory Optimization** [[paper](https://arxiv.org/abs/2603.00871)]
- [2026] **Multi-Agent Motion Planning on Industrial Magnetic Levitation Platforms: A Hybrid ADMM-HOCBF approach** [[paper](https://arxiv.org/abs/2603.19838)]
- [2026] **Graph-of-Constraints Model Predictive Control for Reactive Multi-agent Task and Motion Planning** [[paper](https://arxiv.org/abs/2603.18400)]
- [2026] **ACLM: ADMM-Based Distributed Model Predictive Control for Collaborative Loco-Manipulation** [[paper](https://arxiv.org/abs/2603.07095)]
- [2026] **Information-Theoretic Framework for Self-Adapting Model Predictive Controllers** [[paper](https://arxiv.org/abs/2603.01286)]
- [2026] **Kernel-SDF: An Open-Source Library for Real-Time Signed Distance Function Estimation using Kernel Regression** [[paper](https://arxiv.org/abs/2603.29227)]
- [2026] **Flight through Narrow Gaps with Morphing-Wing Drones** [[paper](https://arxiv.org/abs/2603.12059)]
- [2026] **Toward Generalist Neural Motion Planners for Robotic Manipulators: Challenges and Opportunities** [[paper](https://arxiv.org/abs/2603.24318)]
- [2026] **Rethinking Gaussian Trajectory Predictors: Calibrated Uncertainty for Safe Planning** [[paper](https://arxiv.org/abs/2603.10407)]
- [2026] **ADMM-Based Distributed MPC with Control Barrier Functions for Safe Multi-Robot Quadrupedal Locomotion** [[paper](https://arxiv.org/abs/2603.19170)]
- [2026] **COAD: Constant-Time Planning for Continuous Goal Manipulation with Compressed Library and Online Adaptation** [[paper](https://arxiv.org/abs/2603.12488)]
- [2026] **GAIDE: Graph-based Attention Masking for Spatial- and Embodiment-aware Motion Planning** [[paper](https://arxiv.org/abs/2603.04463)]
- [2026] **Path Planning and Reinforcement Learning-Driven Control of On-Orbit Free-Flying Multi-Arm Robots** [[paper](https://arxiv.org/abs/2603.23182)]
- [2026] **Spatially Grounded Long-Horizon Task Planning in the Wild** [[paper](https://arxiv.org/abs/2603.13433)]
- [2026] **GIANT - Global Path Integration and Attentive Graph Networks for Multi-Agent Trajectory Planning** [[paper](https://arxiv.org/abs/2603.04659)]
- [2026] **Offload or Overload: A Platform Measurement Study of Mobile Robotic Manipulation Workloads** [[paper](https://arxiv.org/abs/2603.18284)]
- [2026] **MA-CoNav: A Master-Slave Multi-Agent Framework with Hierarchical Collaboration and Dual-Level Reflection for Long-Horizon Embodied VLN** [[paper](https://arxiv.org/abs/2603.03024)]
- [2026] **Hybrid Framework for Robotic Manipulation: Integrating Reinforcement Learning and Large Language Models** [[paper](https://arxiv.org/abs/2603.30022)]
- [2026] **Robotic Ultrasound Makes CBCT Alive** [[paper](https://arxiv.org/abs/2603.10220)]
- [2026] **Long-Short Term Agents for Pure-Vision Bronchoscopy Robotic Autonomy** [[paper](https://arxiv.org/abs/2603.07909)]
- [2026] **Review article: A review of control technologies for soft robots: from structural design to intelligent control** *Mechanical sciences* [[paper](https://doi.org/10.5194/ms-17-313-2026)]
- [2026] **A subproblem-based hierarchical framework for multi-AUV cooperative motion planning and robust control** *Ocean Engineering* [[paper](https://doi.org/10.1016/j.oceaneng.2026.125111)]
- [2026] **Machine learning-based motion optimization in intelligent robotic systems** *i-manager’s Journal on Mechanical Engineering* [[paper](https://doi.org/10.26634/jme.16.1.1251)]
- [2026] **Research on Modeling and Energy Consumption Optimization of Humanoid Robot Performance Motions Based on Multi-Stage Trajectory Planning Algorithm** *Journal of Applied AI and Interdisciplinary Innovations* [[paper](https://doi.org/10.64549/jaai-ii.v1i2.8)]
- [2026] **PSO Trajectory Optimization of Robot Arm for Ultrasonic Testing of Complex Curved Surface** *Coatings* [[paper](https://doi.org/10.3390/coatings16030332)]
- [2026] **Optimal trajectory planning for collaborative robots based on improved adaptive multi-objective particle swarm algorithm** *International Journal of Intelligent Robotics and Applications* [[paper](https://doi.org/10.1007/s41315-026-00523-0)]
- [2026] **KINEMATIC MODELING AND TRAJECTORY OPTIMIZATION OF INDUSTRIAL ROBOTIC ARMS USING D-H PARAMETERS, B-SPLINE CURVES, AND GENETIC ALGORITHM** *International Journal of Mechatronics and Applied Mechanics* [[paper](https://doi.org/10.17683/ijomam/issue23.16)]
- [2026] **Non-prehensile Robotic Transportation of Liquid: MPC vs Time-Optimal Trajectory Planning** *AMS Degree Thesis (University of Bologna)* [[paper](https://amslaurea.unibo.it/view/cds/CDS8891/>,)]
- [2026] **Autonomous Navigation Mobile Robot Based on Robot Operating System** [[paper](https://doi.org/10.1201/9781003770497-12)]
- [2026] **ToMPC: Task-oriented Model Predictive Control via ADMM for Safe Robotic Manipulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.13944)]
- [2026] **Decoupled MPPI-Based Multi-Arm Motion Planning** [[paper](https://arxiv.org/abs/2602.10114)]
- [2026] **Strategizing at Speed: A Learned Model Predictive Game for Multi-Agent Drone Racing** [[paper](https://arxiv.org/abs/2602.06925)]
- [2026] **SPOT: Spatio-Temporal Obstacle-free Trajectory Planning for UAVs in Unknown Dynamic Environments** [[paper](https://arxiv.org/abs/2602.01189)]
- [2026] **Dodging the Moose: Experimental Insights in Real-Life Automated Collision Avoidance** [[paper](https://arxiv.org/abs/2602.17512)]
- [2026] **CoReLIN: Constraint-based Reasoning for Zero-shot Lifelong Interactive Navigation** [[paper](https://arxiv.org/abs/2602.20055)]
- [2026] **SuReNav: Superpixel Graph-based Constraint Relaxation for Navigation in Over-constrained Environments** [[paper](https://arxiv.org/abs/2602.06807)]
- [2026] **NovaPlan: Zero-Shot Long-Horizon Manipulation via Closed-Loop Video Language Planning** [[paper](https://arxiv.org/abs/2602.20119)]
- [2026] **From Obstacles to Etiquette: Robot Social Navigation with VLM-Informed Path Selection** [[paper](https://arxiv.org/abs/2602.09002)]
- [2026] **MALLVI: A Multi-Agent Framework for Integrated Generalized Robotics Manipulation** [[paper](https://arxiv.org/abs/2602.16898)]
- [2026] **MolmoSpaces: A Large-Scale Open Ecosystem for Robot Navigation and Manipulation** [[paper](https://arxiv.org/abs/2602.11337)]
- [2026] **Multi Graph Search for High-Dimensional Robot Motion Planning** [[paper](https://arxiv.org/abs/2602.12096)]
- [2026] **Intelligent assembly of shield tunnel lining segments: A vision-guided integrated approach** *Advanced Engineering Informatics* [[paper](https://doi.org/10.1016/j.aei.2026.104460)]
- [2026] **LLM-Driven Scenario-Aware Planning for Autonomous Driving** [[paper](https://arxiv.org/abs/2601.21876)]
- [2026] **HPTune: Hierarchical Proactive Tuning for Collision-Free Model Predictive Control** [[paper](https://arxiv.org/abs/2601.21346)]
- [2026] **Learning Legged MPC with Smooth Neural Surrogates** [[paper](https://arxiv.org/abs/2601.12169)]
- [2026] **Intelligent Singularity Avoidance in UR10 Robotic Arm Path Planning Using Hybrid Fuzzy Logic and Reinforcement Learning** [[paper](https://arxiv.org/abs/2601.05836)]
- [2026] **HumanDiffusion: A Vision-Based Diffusion Trajectory Planner with Human-Conditioned Goals for Search and Rescue UAV** [[paper](https://arxiv.org/abs/2601.14973)]
- [2026] **SceneFoundry: Generating Interactive Infinite 3D Worlds** [[paper](https://arxiv.org/abs/2601.05810)]
- [2026] **Breaking Task Impasses Quickly: Adaptive Neuro-Symbolic Learning for Open-World Robotics** [[paper](https://arxiv.org/abs/2601.16985)]
- [2026] **\textsc{NaVIDA}: Vision-Language Navigation with Inverse Dynamics Augmentation** [[paper](https://arxiv.org/abs/2601.18188)]

##### 2025

- [2025] **ParaMaP: Parallel Mapping and Collision-free Motion Planning for Reactive Robot Manipulation** [[paper](https://arxiv.org/abs/2512.22575)]
- [2025] **Safety Reinforced Model Predictive Control (SRMPC): Improving MPC with Reinforcement Learning for Motion Planning in Autonomous Driving** [[paper](https://arxiv.org/abs/2512.03774)]
- [2025] **Multimodal Control of Manipulators: Coupling Kinematics and Vision for Self-Driving Laboratory Operations** [[paper](https://arxiv.org/abs/2512.03630)]
- [2025] **A Task-Driven, Planner-in-the-Loop Computational Design Framework for Modular Manipulators** [[paper](https://arxiv.org/abs/2512.16069)]
- [2025] **Prediction-Driven Motion Planning: Route Integration Strategies in Attention-Based Prediction Models** [[paper](https://arxiv.org/abs/2512.03756)]
- [2025] **ReinforceGen: Hybrid Skill Policies with Automated Data Generation and Reinforcement Learning** [[paper](https://arxiv.org/abs/2512.16861)]
- [2025] **Results of the 2024 CommonRoad Motion Planning Competition for Autonomous Vehicles** [[paper](https://arxiv.org/abs/2512.19564)]
- [2025] **What Drives Success in Physical Planning with Joint-Embedding Predictive World Models?** [[paper](https://arxiv.org/abs/2512.24497)]
- [2025] **Embodied Tree of Thoughts: Deliberate Manipulation Planning with Embodied World Model** [[paper](https://arxiv.org/abs/2512.08188)]
- [2025] **SimWorld-Robotics: Synthesizing Photorealistic and Dynamic Urban Environments for Multimodal Robot Navigation and Collaboration** [[paper](https://arxiv.org/abs/2512.10046)]
- [2025] **AnyTask: an Automated Task and Data Generation Framework for Advancing Sim-to-Real Policy Learning** [[paper](https://arxiv.org/abs/2512.17853)]
- [2025] **XR-DT: Extended Reality-Enhanced Digital Twin for Safe Motion Planning via Human-Aware Model Predictive Path Integral Control** [[paper](https://arxiv.org/abs/2512.05270)]
- [2025] **Exact Smooth Reformulations for Trajectory Optimization Under Signal Temporal Logic Specifications** [[paper](https://arxiv.org/abs/2511.07375)]
- [2025] **DPNet: Doppler LiDAR Motion Planning for Highly-Dynamic Environments** [[paper](https://arxiv.org/abs/2512.00375)]
- [2025] **Manifold-constrained Hamilton-Jacobi Reachability Learning for Decentralized Multi-Agent Motion Planning** [[paper](https://arxiv.org/abs/2511.03591)]
- [2025] **High-Altitude Balloon Station-Keeping with First Order Model Predictive Control** [[paper](https://arxiv.org/abs/2511.07761)]
- [2025] **Asynchronous Distributed Multi-Robot Motion Planning Under Imperfect Communication** [[paper](https://arxiv.org/abs/2511.18703)]
- [2025] **Scalable Coverage Trajectory Synthesis on GPUs as Statistical Inference** [[paper](https://arxiv.org/abs/2511.11514)]
- [2025] **Hessians in Birkhoff-Theoretic Trajectory Optimization** [[paper](https://arxiv.org/abs/2511.13963)]
- [2025] **BINDER: Instantly Adaptive Mobile Manipulation with Open-Vocabulary Commands** [[paper](https://arxiv.org/abs/2511.22364)]
- [2025] **Affordance-Guided Coarse-to-Fine Exploration for Base Placement in Open-Vocabulary Mobile Manipulation** [[paper](https://arxiv.org/abs/2511.06240)]
- [2025] **Constant-Time Motion Planning with Manipulation Behaviors** [[paper](https://arxiv.org/abs/2512.00939)]
- [2025] **Voice-Interactive Surgical Agent for Multimodal Patient Data Control** [[paper](https://arxiv.org/abs/2511.07392)]
- [2025] **Think, Remember, Navigate: Zero-Shot Object-Goal Navigation with VLM-Powered Reasoning** [[paper](https://arxiv.org/abs/2511.08942)]
- [2025] **Safe Motion Planning and Control Using Predictive and Adaptive Barrier Methods for Autonomous Surface Vessels** [[paper](https://arxiv.org/abs/2510.01357)]
- [2025] **MPC-based motion planning for non-holonomic systems in non-convex domains** [[paper](https://arxiv.org/abs/2510.18402)]
- [2025] **Load-bearing Assessment for Safe Locomotion of Quadruped Robots on Collapsing Terrain** [[paper](https://arxiv.org/abs/2510.21369)]
- [2025] **Integrated Planning and Control on Manifolds: Factor Graph Representation and Toolkit** [[paper](https://arxiv.org/abs/2510.04278)]
- [2025] **Point Cloud-Based Control Barrier Functions for Model Predictive Control in Safety-Critical Navigation of Autonomous Mobile Robots** [[paper](https://arxiv.org/abs/2510.02885)]
- [2025] **GATO: GPU-Accelerated and Batched Trajectory Optimization for Scalable Edge Model Predictive Control** [[paper](https://arxiv.org/abs/2510.07625)]
- [2025] **Real-Time QP Solvers: A Concise Review and Practical Guide Towards Legged Robots** [[paper](https://arxiv.org/abs/2510.21773)]
- [2025] **Push Anything: Single- and Multi-Object Pushing From First Sight with Contact-Implicit MPC** [[paper](https://arxiv.org/abs/2510.19974)]
- [2025] **PAD-TRO: Projection-Augmented Diffusion for Direct Trajectory Optimization** [[paper](https://arxiv.org/abs/2510.04436)]
- [2025] **NovaFlow: Zero-Shot Manipulation via Actionable Flow from Generated Videos** [[paper](https://arxiv.org/abs/2510.08568)]
- [2025] **Traj2Action: A Co-Denoising Framework for Trajectory-Guided Human-to-Robot Skill Transfer** [[paper](https://arxiv.org/abs/2510.00491)]
- [2025] **Executable Analytic Concepts as the Missing Link Between VLM Insight and Precise Manipulation** [[paper](https://arxiv.org/abs/2510.07975)]
- [2025] **VAMOS: A Hierarchical Vision-Language-Action Model for Capability-Modulated and Steerable Navigation** [[paper](https://arxiv.org/abs/2510.20818)]
- [2025] **Information Seeking for Robust Decision Making under Partial Observability** [[paper](https://arxiv.org/abs/2510.01531)]
- [2025] **GRIP: A Unified Framework for Grid-Based Relay and Co-Occurrence-Aware Planning in Dynamic Environments** [[paper](https://arxiv.org/abs/2510.10865)]
- [2025] **RoboGPT-R1: Enhancing Robot Task Planning with Reinforcement Learning** [[paper](https://arxiv.org/abs/2510.14828)]
- [2025] **ManiAgent: An Agentic Framework for General Robotic Manipulation** [[paper](https://arxiv.org/abs/2510.11660)]
- [2025] **BLAZER: Bootstrapping LLM-based Manipulation Agents with Zero-Shot Data Generation** [[paper](https://arxiv.org/abs/2510.08572)]
- [2025] **UrbanVLA: A Vision-Language-Action Model for Urban Micromobility** [[paper](https://arxiv.org/abs/2510.23576)]
- [2025] **An Intention-driven Lane Change Framework Considering Heterogeneous Dynamic Cooperation in Mixed-traffic Environment** [[paper](https://arxiv.org/abs/2509.22550)]
- [2025] **The Trajectory Bundle Method: Unifying Sequential-Convex Programming and Sampling-Based Trajectory Optimization** [[paper](https://arxiv.org/abs/2509.26575)]
- [2025] **An MPC framework for efficient navigation of mobile robots in cluttered environments** [[paper](https://arxiv.org/abs/2509.15917)]
- [2025] **Safe Robust Predictive Control-based Motion Planning of Automated Surface Vessels in Inland Waterways** [[paper](https://arxiv.org/abs/2509.06687)]
- [2025] **BagIt! An Adaptive Dual-Arm Manipulation of Fabric Bags for Object Bagging** [[paper](https://arxiv.org/abs/2509.09484)]
- [2025] **ORB: Operating Room Bot, Automating Operating Room Logistics through Mobile Manipulation** [[paper](https://arxiv.org/abs/2509.15600)]
- [2025] **SRMP: Search-Based Robot Motion Planning Library** [[paper](https://arxiv.org/abs/2509.25352)]
- [2025] **First Plan Then Evaluate: Multi-Target Planning with Post-Planning Success Evaluation Improves Learning-Based Grasping Pipelines** [[paper](https://arxiv.org/abs/2509.07162)]
- [2025] **Generalizing Multi-Objective Search via Objective-Aggregation Functions** [[paper](https://arxiv.org/abs/2509.22085)]
- [2025] **Learning Social Heuristics for Human-Aware Path Planning** [[paper](https://arxiv.org/abs/2509.02134)]
- [2025] **Memory Transfer Planning: LLM-driven Context-Aware Code Adaptation for Robot Manipulation** [[paper](https://arxiv.org/abs/2509.24160)]
- [2025] **TANGO: Traversability-Aware Navigation with Local Metric Control for Topological Goals** [[paper](https://arxiv.org/abs/2509.08699)]
- [2025] **RoboPilot: Generalizable Dynamic Robotic Manipulation with Dual-thinking Modes** [[paper](https://arxiv.org/abs/2510.00154)]
- [2025] **Message passing-based inference in an autoregressive active inference agent** [[paper](https://arxiv.org/abs/2509.25482)]
- [2025] **A Design Co-Pilot for Task-Tailored Manipulators** [[paper](https://arxiv.org/abs/2509.13077)]
- [2025] **RAVEN: Resilient Aerial Navigation via Open-Set Semantic Memory and Behavior Adaptation** [[paper](https://arxiv.org/abs/2509.23563)]
- [2025] **Dynamic Buffers: Cost-Efficient Planning for Tabletop Rearrangement with Stacking** [[paper](https://arxiv.org/abs/2509.22828)]
- [2025] **SafeFlowMatcher: Safe and Fast Planning using Flow Matching with Control Barrier Functions** [[paper](https://arxiv.org/abs/2509.24243)]
- [2025] **Regulation-Aware Game-Theoretic Motion Planning for Autonomous Racing** [[paper](https://arxiv.org/abs/2508.20203)]
- [2025] **Robust Convex Model Predictive Control with collision avoidance guarantees for robot manipulators** [[paper](https://arxiv.org/abs/2508.21677)]
- [2025] **ManipDreamer3D : Synthesizing Plausible Robotic Manipulation Video with Occupancy-aware 3D Trajectory** [[paper](https://arxiv.org/abs/2509.05314)]
- [2025] **Jacobian Exploratory Dual-Phase Reinforcement Learning for Dynamic Endoluminal Navigation of Deformable Continuum Robots** [[paper](https://arxiv.org/abs/2509.00329)]
- [2025] **Scalable Solution Methods for Dec-POMDPs with Deterministic Dynamics** [[paper](https://arxiv.org/abs/2508.21595)]
- [2025] **Real-Time Model Checking for Closed-Loop Robot Reactive Planning** [[paper](https://arxiv.org/abs/2508.19186)]
- [2025] **NeuralSVCD for Efficient Swept Volume Collision Detection** [[paper](https://arxiv.org/abs/2509.00499)]

[⬆ Back to top](#paper-list)

#### Development

##### 2026

- [2026] **augmentedfabricationlab/mobile_motion_planning: Mobile Motion Planning v0.1.0 - Initial Release** *Open MIND* [[paper](https://github.com/augmentedfabricationlab/mobile_motion_planning/tree/v0.1.0)]

[⬆ Back to top](#paper-list)

### Learning & Adaptation

#### Theory

##### 2026

- [2026] **Applications of Reinforcement Learning for Autonomous Surgical Robotics: A Systematic Review** *Biomimetics* [[paper](https://doi.org/10.3390/biomimetics11080577)]
- [2026] **VL-I2O: Vision-Language Assisted Imitation-to-Optimization Reinforcement Learning for Robot Manipulation** *Lecture notes in computer science* [[paper](https://doi.org/10.1007/978-981-92-3441-7_20)]
- [2026] **Enhancing deep reinforcement learning with expert demonstrations for mobile robot navigation in unstructured off-road environments** *Research Online (Edith Cowan University)* [[paper](https://ro.ecu.edu.au/theses/3089)]
- [2026] **Impact of Continuous Latent Variables on Imitation Learning Efficiency and Stability** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20651591)]
- [2026] **Enhancing autonomous navigation systems through reinforcement learning** *Automatika* [[paper](https://doi.org/10.1080/00051144.2026.2688597)]
- [2026] **Editorial: Innovations in industry 4.0: advancing mobility and manipulation in robotics** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1889141)]
- [2026] **From False Positives to Failure Topologies: Heuristic Learning for Auditable Dexterous Grasping Development** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20729635)]
- [2026] **Single-Demonstration Imitation with Residual Reinforcement Learning for Dual-Arm Robotic Bottle Opening** *Simposios del Comité Español de Automática (CEA)* [[paper](https://doi.org/10.64117/simposioscea.v2i2.209)]
- [2026] **Editorial: Reinforcement learning for real-world robot navigation** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1861947)]
- [2026] **Toward Reliable Vision-Driven UAV River Navigation: Human-Informed Safe Learning and Navigability Mapping** *Purdue* [[paper](https://doi.org/10.25394/pgs.32125114)]
- [2026] **KinDER: A Physical Reasoning Benchmark for Robot Learning and Planning** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.25788)]
- [2026] **Learning from Imperfect Demonstrations via Temporal Behavior Tree-Guided Trajectory Repair** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.04225)]
- [2026] **VIGOR: Visual Goal-In-Context Inference for Unified Humanoid Fall Safety** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2602.16511)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **ODARRL: Obstacle- and Disturbance-Aware End-to-End Residual Reinforcement Learning for Underwater Robot Trajectory Tracking with Obstacle Avoidance** *Journal of Marine Science and Engineering* [[paper](https://doi.org/10.3390/jmse14161501)]
- [2026] **One Demonstration Is Enough for Real-World Robotic Reinforcement Learning** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.01651)]
- [2026] **AI-driven precision: Reinforcement learning-based control for microscope-assisted robotic retina surgery** *AIP Advances* [[paper](https://doi.org/10.1063/5.0341159)]
- [2026] **A graph isomorphism attention network and graph information embedded reinforcement learning-based dual-arm robot teleoperation and manipulation skill acquisition method** *Journal of Manufacturing Systems* [[paper](https://doi.org/10.1016/j.jmsy.2026.06.023)]
- [2026] **Designing A Learning-Enabled Non-Anthropomorphic Robotic Hand Framework for Dexterous Manipulation** *KiltHub Repository* [[paper](https://doi.org/10.1184/r1/32984639.v1)]
- [2026] **OopsieVerse: A Safety Benchmark with Damage-Aware Simulation for Robot Manipulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.31993)]
- [2026] **Humanoid Robot Walking and Grasping Method Using Similarity Reward-Augmented Generative Adversarial Imitation Learning** *Sensors* [[paper](https://doi.org/10.3390/s26092756)]
- [2026] **Learning to switch safely: terrain-adaptive humanoid locomotion acquisition via hard-routed mixture-of-expert motion imitation** [[paper](https://doi.org/10.1117/12.3111151)]
- [2026] **Learn Weightlessness: Imitate Non-Self-Stabilizing Motions on Humanoid Robot** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.21351)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **SAFE-CHEM: Uncertainty-Aware Policy Switching for Robust Robotic Chemistry** [[paper](https://arxiv.org/abs/2608.09303)]
- [2026] **Combining exploration and imitation in contact-rich task learning on an articulated soft robot arm** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1885625)]
- [2026] **Joint On-and-Off Policy Learning for Vision-and-Language Navigation** [[paper](https://arxiv.org/abs/2607.13461)]
- [2026] **EA-Nav: Learning Safe Visual Navigation Policies with Embodiment Awareness** [[paper](https://arxiv.org/abs/2607.19880)]
- [2026] **LAMP: Latent Motion Prior-Guided Real-World Learning for Dexterous Hand Manipulation** [[paper](https://arxiv.org/abs/2607.06323)]
- [2026] **Semantic Audio-driven Understanding for Dynamic Humanoid Whole Body Control** [[paper](https://arxiv.org/abs/2607.14182)]
- [2026] **DenseReward: Dense Reward Learning via Failure Synthesis for Robotic Manipulation** [[paper](https://arxiv.org/abs/2607.13033)]
- [2026] **SILO: Simulation-in-the-Loop Sim-to-Real Transfer for Multi-Stage Cable Routing** [[paper](https://arxiv.org/abs/2607.04616)]
- [2026] **PRISM: Polynomial Representations for Interaction-Structured Motor Control** [[paper](https://arxiv.org/abs/2607.23473)]
- [2026] **SIEVE: Structure-Aware Data Selection for Imitation Learning with VLA Models** [[paper](https://arxiv.org/abs/2607.06442)]
- [2026] **A Minimalist Retargeting-Guided Reinforcement Learning Recipe for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2607.11874)]
- [2026] **Towards Miniature Humanoid Tele-Loco-Manipulation Using Virtual Reality and Reinforcement Learning** [[paper](https://arxiv.org/abs/2607.20399)]
- [2026] **Action Map Policy: Learning 3D Closed-loop Manipulation via Pixel Classification** [[paper](https://arxiv.org/abs/2607.10706)]
- [2026] **Teaching Tiny VLA Models Where to Look and How to Move** [[paper](https://arxiv.org/abs/2607.04171)]
- [2026] **Task-Relevant Representation Decoupling for Visual Reinforcement Learning Generalization** [[paper](https://arxiv.org/abs/2607.00796)]
- [2026] **SymmGrid: Super-Scaling On-Robot Learning with Parallelized Symmetries and Egocentric-Exocentric Visual Perception** [[paper](https://arxiv.org/abs/2607.26985)]
- [2026] **Learning Task-Sufficient World Models by Synergizing Agentic Exploration and Structured Modeling** [[paper](https://arxiv.org/abs/2607.04409)]
- [2026] **GenVid2Robot: From Video Generation to Robot Manipulation via Rigid-Geometric Consistency** [[paper](https://arxiv.org/abs/2607.09191)]
- [2026] **Performant robotic manipulation with real-world reinforcement learning** *Science Robotics* [[paper](https://doi.org/10.1126/scirobotics.aed6267)]
- [2026] **WorldSample: Closed-loop Real-robot RL with World Modelling** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.02431)]
- [2026] **CLIFT: Turning Gemini Robotics On-Device into Humanoid Specialists via Non-Invasive Closed-Loop Iterative Fine-Tuning** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.29172)]
- [2026] **Temporal Self-Imitation Learning** [[paper](https://arxiv.org/abs/2606.19752)]
- [2026] **RE4: Transformation-aware Imitation of Object Interactions Using Manipulation Modes** [[paper](https://arxiv.org/abs/2606.24403)]
- [2026] **Reinforcement Learning-Guided Retrieval with Soft Fusion for Robust Multimodal Imitation Learning under Missing Modalities** [[paper](https://arxiv.org/abs/2606.15514)]
- [2026] **Trajectory Learning with Graph Representations for Social Robot Navigation** [[paper](https://arxiv.org/abs/2607.00028)]
- [2026] **HiL-ResRL: A Model-Agnostic Finetuning Adapter via Human-in-the-loop Residual Reinforcement Learning** [[paper](https://arxiv.org/abs/2606.22860)]
- [2026] **Kine2Go: Kinematic dataset for the Unitree Go2 robot with diverse gaits and motions** [[paper](https://arxiv.org/abs/2606.14433)]
- [2026] **Reinforcement Learning-Based Control for an Inline Skating Humanoid Robot** [[paper](https://arxiv.org/abs/2606.31807)]
- [2026] **What Probing Reveals about Autonomous Driving: Linking Internal Prediction Errors to Ego Planning** [[paper](https://arxiv.org/abs/2606.31106)]
- [2026] **Difference-Aware Retrieval Policies for Imitation Learning** [[paper](https://arxiv.org/abs/2606.09758)]
- [2026] **MoDex: A Diffusion Policy for Sequential Multi-Object Dexterous Grasping** [[paper](https://arxiv.org/abs/2606.05407)]
- [2026] **Trust Your Instincts: Confidence-Driven Test-Time RL for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2606.29892)]
- [2026] **MPC-Injection: Biasing Off-Policy Locomotion RL Toward Controller-Induced Behavior Basins** [[paper](https://arxiv.org/abs/2606.26392)]
- [2026] **ORCA: A Platform for Open-Source Dexterity Research** [[paper](https://arxiv.org/abs/2606.14561)]
- [2026] **A New Quaternion-Joint Cable-Driven Redundant Manipulator Configuration and its Control Through FABRIK and Residual Reinforcement Learning** [[paper](https://arxiv.org/abs/2606.05236)]
- [2026] **Learning Object Manipulation from Scratch via Contrastive Interaction** [[paper](https://arxiv.org/abs/2606.11525)]
- [2026] **LadderMan: Learning Humanoid Perceptive Ladder Climbing** [[paper](https://arxiv.org/abs/2606.05873)]
- [2026] **What Matters in Orchestrating Robot Policies: A Systematic Study of Hierarchical VLA Agents** [[paper](https://arxiv.org/abs/2606.10267)]
- [2026] **GHOST: Hierarchical Sub-Goal Policies for Generalizing Robot Manipulation** [[paper](https://arxiv.org/abs/2606.10025)]
- [2026] **Coherent Off-Policy Improvement of Large Behavior Models with Learned Rewards** [[paper](https://arxiv.org/abs/2606.02194)]
- [2026] **Dexterous Point Policy: Learning Point-based Dexterous Hand Policies from Human Demonstrations** [[paper](https://arxiv.org/abs/2606.10614)]
- [2026] **Universal Manipulation Exoskeleton: Learning Compliant Whole-body Policies with Real-time Torque Feedback** [[paper](https://arxiv.org/abs/2606.14218)]
- [2026] **DIRA: Diffusion-Based Imitation-to-Reinforcement Adaptation for Task Automation of Surgical Robots** *IEEE Robotics and Automation Letters* [[paper](https://doi.org/10.1109/lra.2026.3699185)]
- [2026] **Object-Centric Residual RL for Zero-Shot Sim-to-Real VLA Enhancement** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.18953)]
- [2026] **ReActor: Reinforcement Learning for Physics-Aware Motion Retargeting** [[paper](https://arxiv.org/abs/2605.06593)]
- [2026] **Feat2Go: Visual Feature-Grounded Value Estimation for Embodied Reinforcement Learning** [[paper](https://arxiv.org/abs/2605.30795)]
- [2026] **NavOL: Navigation Policy with Online Imitation Learning** [[paper](https://arxiv.org/abs/2605.11762)]
- [2026] **Learning Bilevel Policies over Symbolic World Models for Long-Horizon Planning** [[paper](https://arxiv.org/abs/2605.15975)]
- [2026] **Trust Region Inverse Reinforcement Learning: Explicit Dual Ascent using Local Policy Updates** [[paper](https://arxiv.org/abs/2605.11020)]
- [2026] **HOIST: Humanoid Optimization with Imitation and Sample-efficient Tuning for Manipulating Suspended Loads** [[paper](https://arxiv.org/abs/2606.00252)]
- [2026] **ParkingWorld: End-to-End Autonomous Parking Reinforcement Learning from Corrective Experience in 3DGS Simulation** [[paper](https://arxiv.org/abs/2605.25029)]
- [2026] **Teacher-Student Representational Alignment for Reinforcement Learning-Driven Imitation Learning** [[paper](https://arxiv.org/abs/2605.28372)]
- [2026] **Constraint-Aware Diffusion Priors for High-Fidelity and Versatile Quadruped Locomotion** [[paper](https://arxiv.org/abs/2605.08804)]
- [2026] **From Reach to Insert: Tactile-Augmented Precision Assembly under Sub-Millimeter Tolerances** [[paper](https://arxiv.org/abs/2605.04649)]
- [2026] **Instrumentation for Imitation Learning: Enhancing Training Datasets for Clothes Hanger Insertion** [[paper](https://arxiv.org/abs/2605.23847)]
- [2026] **WarmPrior: Straightening Flow-Matching Policies with Temporal Priors** [[paper](https://arxiv.org/abs/2605.13959)]
- [2026] **DynaFLIP: Rethinking Robotics Perception via Tri-Modal-Dynamics Guided Representation** [[paper](https://arxiv.org/abs/2605.30350)]
- [2026] **RLDX-1 Technical Report** [[paper](https://arxiv.org/abs/2605.03269)]
- [2026] **ProgVLA: Progress-Aware Robot Manipulation Skill Learning** [[paper](https://arxiv.org/abs/2605.28231)]
- [2026] **TMRL: Diffusion Timestep-Modulated Pretraining Enables Exploration for Efficient Policy Finetuning** [[paper](https://arxiv.org/abs/2605.12236)]
- [2026] **Survival Reinforcement Learning: Toward Scalable Self-Supervised RL** [[paper](https://arxiv.org/abs/2605.31273)]
- [2026] **Behavior Cloning of MPC for 3-DOF Robotic Manipulators** [[paper](https://arxiv.org/abs/2606.00383)]
- [2026] **Optimizing Neurorobot Policy under Limited Demonstration Data through Preference Regret** [[paper](https://arxiv.org/abs/2604.03523)]
- [2026] **Simulation of Adaptive Running with Flexible Sports Prosthesis using Reinforcement Learning of Hybrid-link System** [[paper](https://arxiv.org/abs/2604.08882)]
- [2026] **HTNav: A Hybrid Navigation Framework with Tiered Structure for Urban Aerial Vision-and-Language Navigation** [[paper](https://arxiv.org/abs/2604.08883)]
- [2026] **MoRI: Mixture of RL and IL Experts for Long-Horizon Manipulation Tasks** [[paper](https://arxiv.org/abs/2604.10165)]
- [2026] **BAT: Balancing Agility and Stability via Online Policy Switching for Long-Horizon Whole-Body Humanoid Control** [[paper](https://arxiv.org/abs/2604.01064)]
- [2026] **ScoRe-Flow: Complete Distributional Control via Score-Based Reinforcement Learning for Flow Matching** [[paper](https://arxiv.org/abs/2604.10962)]
- [2026] **Behavior-Constrained Reinforcement Learning with Receding-Horizon Credit Assignment for High-Performance Control** [[paper](https://arxiv.org/abs/2604.03023)]
- [2026] **GSDrive: Reinforcing Driving Policies by Multi-mode Future Trajectory Probing with 3D Gaussian Splatting Environment** [[paper](https://arxiv.org/abs/2604.28111)]
- [2026] **Deep Reinforcement Learning for Robotic Manipulation under Distribution Shift with Bounded Extremum Seeking** [[paper](https://arxiv.org/abs/2604.01142)]
- [2026] **AIM: Intent-Aware Unified world action Modeling with Spatial Value Maps** [[paper](https://arxiv.org/abs/2604.11135)]
- [2026] **Learning-augmented robotic automation for real-world manufacturing** [[paper](https://arxiv.org/abs/2604.22235)]
- [2026] **Learning from Demonstration with Failure Awareness for Safe Robot Navigation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.23360)]
- [2026] **Reinforcement Learning in Robotics Bionic Arm Control and Adaptation** *University of Debrecen Electronic Archive (University of Debrecen)* [[paper](https://hdl.handle.net/2437/413147)]
- [2026] **Vision-driven state-space imitation learning for quadrotor navigation in infrastructure inspection** *Computer-Aided Civil and Infrastructure Engineering* [[paper](https://doi.org/10.1016/j.cacaie.2026.100030)]
- [2026] **Generative adversarial imitation learning for robot swarms: Learning from human demonstrations and trained policies** [[paper](https://arxiv.org/abs/2603.02783)]
- [2026] **Fine-tuning is Not Enough: A Parallel Framework for Collaborative Imitation and Reinforcement Learning in End-to-end Autonomous Driving** [[paper](https://arxiv.org/abs/2603.13842)]
- [2026] **ScanDP: Generalizable 3D Scanning with Diffusion Policy** [[paper](https://arxiv.org/abs/2603.10390)]
- [2026] **Devil is in Narrow Policy: Unleashing Exploration in Driving VLA Models** [[paper](https://arxiv.org/abs/2603.06049)]
- [2026] **Minimalist Compliance Control** [[paper](https://arxiv.org/abs/2603.00913)]
- [2026] **PRISM: Personalized Refinement of Imitation Skills for Manipulation via Human Instructions** [[paper](https://arxiv.org/abs/2603.05574)]
- [2026] **Beyond Imitation: Reinforcement Learning Fine-Tuning for Adaptive Diffusion Navigation Policies** [[paper](https://arxiv.org/abs/2603.12868)]
- [2026] **KiRAS: Keyframe Guided Self-Imitation for Robust and Adaptive Skill Learning in Quadruped Robots** [[paper](https://arxiv.org/abs/2603.15179)]
- [2026] **CorrectionPlanner: Self-Correction Planner with Reinforcement Learning in Autonomous Driving** [[paper](https://arxiv.org/abs/2603.15771)]
- [2026] **Efficient and Reliable Teleoperation through Real-to-Sim-to-Real Shared Autonomy** [[paper](https://arxiv.org/abs/2603.17016)]
- [2026] **SSP: Safety-guaranteed Surgical Policy via Joint Optimization of Behavioral and Spatial Constraints** [[paper](https://arxiv.org/abs/2603.07032)]
- [2026] **REFINE-DP: Diffusion Policy Fine-tuning for Humanoid Loco-manipulation via Reinforcement Learning** [[paper](https://arxiv.org/abs/2603.13707)]
- [2026] **Act-Observe-Rewrite: Multimodal Coding Agents as In-Context Policy Learners for Robot Manipulation** [[paper](https://arxiv.org/abs/2603.04466)]
- [2026] **Shape-Interpretable Visual Self-Modeling Enables Geometry-Aware Continuum Robot Control** [[paper](https://arxiv.org/abs/2603.01751)]
- [2026] **Evidence of an Emergent "Self" in Continual Robot Learning** [[paper](https://arxiv.org/abs/2603.24350)]
- [2026] **A Real-Time Neuro-Symbolic Ethical Governor for Safe Decision Control in Autonomous Robotic Manipulation** [[paper](https://arxiv.org/abs/2603.14221)]
- [2026] **MEM: Multi-Scale Embodied Memory for Vision Language Action Models** [[paper](https://arxiv.org/abs/2603.03596)]
- [2026] **ManiTwin: Scaling Data-Generation-Ready Digital Object Dataset to 100K** [[paper](https://arxiv.org/abs/2603.16866)]
- [2026] **Hybrid Data Curation for Imitation Learning with Physics- Generated Trajectories** *Applied Sciences* [[paper](https://doi.org/10.3390/app16062968)]
- [2026] **TW-CRL: Time-Weighted Contrastive Reward Learning for Efficient Inverse Reinforcement Learning** *Proceedings of the AAAI Conference on Artificial Intelligence* [[paper](https://doi.org/10.1609/aaai.v40i28.39499)]
- [2026] **A simulation study of decomposition-based inverse reinforcement learning toward construction automation: The case of excavator in challenging environments** *Developments in the Built Environment* [[paper](https://doi.org/10.1016/j.dibe.2026.100908)]
- [2026] **SutureFormer: Learning Surgical Trajectories via Goal-conditioned Offline RL in Pixel Space** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.26720)]
- [2026] **AdaptManip: Learning Adaptive Whole-Body Object Lifting and Delivery with Online Recurrent State Estimation** [[paper](https://arxiv.org/abs/2602.14363)]
- [2026] **GRAIL: Goal Recognition Alignment through Imitation Learning** [[paper](https://arxiv.org/abs/2602.14252)]
- [2026] **Human-to-Robot Interaction: Learning from Video Demonstration for Robot Imitation** [[paper](https://arxiv.org/abs/2602.19184)]
- [2026] **MePoly: Max Entropy Polynomial Policy Optimization** [[paper](https://arxiv.org/abs/2602.17832)]
- [2026] **RFS: Reinforcement Learning with Residual Flow Steering for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2602.01789)]
- [2026] **WoVR: World Models as Reliable Simulators for Post-Training VLA Policies with RL** [[paper](https://arxiv.org/abs/2602.13977)]
- [2026] **TIC-VLA: A Think-in-Control Vision-Language-Action Model for Robot Navigation in Dynamic Environments** [[paper](https://arxiv.org/abs/2602.02459)]
- [2026] **Diverse Skill Discovery for Quadruped Robots via Unsupervised Learning** [[paper](https://arxiv.org/abs/2602.09767)]
- [2026] **PMG: Parameterized Motion Generator for Human-like Locomotion Control** [[paper](https://arxiv.org/abs/2602.12656)]
- [2026] **Humanoid Manipulation Interface: Humanoid Whole-Body Manipulation from Robot-Free Demonstrations** [[paper](https://arxiv.org/abs/2602.06643)]
- [2026] **YOR: Your Own Mobile Manipulator for Generalizable Robotics** [[paper](https://arxiv.org/abs/2602.11150)]
- [2026] **Imitating What Works: Simulation-Filtered Modular Policy Learning from Human Videos** [[paper](https://arxiv.org/abs/2602.13197)]
- [2026] **Dex4D: Task-Agnostic Point Track Policy for Sim-to-Real Dexterous Manipulation** [[paper](https://arxiv.org/abs/2602.15828)]
- [2026] **Scalable Dexterous Robot Learning with AR-based Remote Human-Robot Interactions** [[paper](https://arxiv.org/abs/2602.07341)]
- [2026] **Learning Part-Aware Dense 3D Feature Field for Generalizable Articulated Object Manipulation** [[paper](https://arxiv.org/abs/2602.14193)]
- [2026] **Primary-Fine Decoupling for Action Generation in Robotic Imitation** [[paper](https://arxiv.org/abs/2602.21684)]
- [2026] **Latent Diffeomorphic Co-Design of End-Effectors for Deformable and Fragile Object Manipulation** [[paper](https://arxiv.org/abs/2602.17921)]
- [2026] **IRIS: Learning-Driven Task-Specific Cinema Robot Arm for Visuomotor Motion Control** [[paper](https://arxiv.org/abs/2602.17537)]
- [2026] **An ensemble reinforcement learning framework for robotic high-precision peg-in-hole assembly via human demonstrations** *Robotics and Computer-Integrated Manufacturing* [[paper](https://doi.org/10.1016/j.rcim.2026.103279)]
- [2026] **MetaWorld: Skill Transfer and Composition in a Hierarchical World Model for Grounding High-Level Instructions** [[paper](https://arxiv.org/abs/2601.17507)]
- [2026] **Task-Centric Policy Optimization from Misaligned Motion Priors** [[paper](https://arxiv.org/abs/2601.19411)]
- [2026] **CLAMP: Contrastive Learning for 3D Multi-View Action-Conditioned Robotic Manipulation Pretraining** [[paper](https://arxiv.org/abs/2602.00937)]
- [2026] **Demonstration-Free Robotic Control via LLM Agents** [[paper](https://arxiv.org/abs/2601.20334)]
- [2026] **ConceptACT: Episode-Level Concepts for Sample-Efficient Robotic Imitation Learning** [[paper](https://arxiv.org/abs/2601.17135)]
- [2026] **MARVL: Multi-Stage Guidance for Robotic Manipulation via Vision-Language Models** [[paper](https://arxiv.org/abs/2602.15872)]

##### 2025

- [2025] **An Introduction to Deep Reinforcement and Imitation Learning** [[paper](https://arxiv.org/abs/2512.08052)]
- [2025] **MindDrive: A Vision-Language-Action Model for Autonomous Driving via Online Reinforcement Learning** [[paper](https://arxiv.org/abs/2512.13636)]
- [2025] **Learning Generalizable Hand-Object Tracking from Synthetic Demonstrations** [[paper](https://arxiv.org/abs/2512.19583)]
- [2025] **A Review of Learning-Based Motion Planning: Toward a Data-Driven Optimal Control Approach** [[paper](https://arxiv.org/abs/2512.11944)]
- [2025] **Post-Training and Test-Time Scaling of Generative Agent Behavior Models for Interactive Autonomous Driving** [[paper](https://arxiv.org/abs/2512.13262)]
- [2025] **Pseudo-Expert Regularized Offline RL for End-to-End Autonomous Driving in Photorealistic Closed-Loop Environments** [[paper](https://arxiv.org/abs/2512.18662)]
- [2025] **RoboMIND 2.0: A Multimodal, Bimanual Mobile Manipulation Dataset for Generalizable Embodied Intelligence** [[paper](https://arxiv.org/abs/2512.24653)]
- [2025] **House of Dextra: Cross-embodied Co-design for Dexterous Hands** [[paper](https://arxiv.org/abs/2512.03743)]
- [2025] **CHIP: Adaptive Compliance for Humanoid Control through Hindsight Perturbation** [[paper](https://arxiv.org/abs/2512.14689)]
- [2025] **Iterative Compositional Data Generation for Robot Control** [[paper](https://arxiv.org/abs/2512.10891)]
- [2025] **Real-World Reinforcement Learning of Active Perception Behaviors** [[paper](https://arxiv.org/abs/2512.01188)]
- [2025] **Real-World Robot Control by Deep Active Inference With a Temporally Hierarchical World Model** [[paper](https://arxiv.org/abs/2512.01924)]
- [2025] **Coordinated Humanoid Manipulation with Choice Policies** [[paper](https://arxiv.org/abs/2512.25072)]
- [2025] **OSMO: Open-Source Tactile Glove for Human-to-Robot Skill Transfer** [[paper](https://arxiv.org/abs/2512.08920)]
- [2025] **Structured Imitation Learning of Interactive Policies through Inverse Games** [[paper](https://arxiv.org/abs/2511.12848)]
- [2025] **LAOF: Robust Latent Action Learning with Optical Flow Constraints** [[paper](https://arxiv.org/abs/2511.16407)]
- [2025] **Dexterous Robotic Piano Playing at Scale** [[paper](https://arxiv.org/abs/2511.02504)]
- [2025] **Temporal Action Selection for Action Chunking** [[paper](https://arxiv.org/abs/2511.04421)]
- [2025] **Gentle Manipulation Policy Learning via Demonstrations from VLM Planned Atomic Skills** [[paper](https://arxiv.org/abs/2511.05855)]
- [2025] **ViPRA: Video Prediction for Robot Actions** [[paper](https://arxiv.org/abs/2511.07732)]
- [2025] **Self-Supervised Multisensory Pretraining for Contact-Rich Robot Reinforcement Learning** [[paper](https://arxiv.org/abs/2511.14427)]
- [2025] **Learning-based Cooperative Robotic Paper Wrapping: A Unified Control Policy with Residual Force Control** [[paper](https://arxiv.org/abs/2511.03181)]
- [2025] **AVA-VLA: Improving Vision-Language-Action models with Active Visual Attention** [[paper](https://arxiv.org/abs/2511.18960)]
- [2025] **Dexterity from Smart Lenses: Multi-Fingered Robot Manipulation with In-the-Wild Human Demonstrations** [[paper](https://arxiv.org/abs/2511.16661)]
- [2025] **TWIST2: Scalable, Portable, and Holistic Humanoid Data Collection System** [[paper](https://arxiv.org/abs/2511.02832)]
- [2025] **SpeedAug: Policy Acceleration via Tempo-Enriched Policy and RL Fine-Tuning** [[paper](https://arxiv.org/abs/2512.00062)]
- [2025] **EL3DD: Extended Latent 3D Diffusion for Language Conditioned Multitask Manipulation** [[paper](https://arxiv.org/abs/2511.13312)]
- [2025] **Real-to-Sim Robot Policy Evaluation with Gaussian Splatting Simulation of Soft-Body Interactions** [[paper](https://arxiv.org/abs/2511.04665)]
- [2025] **Using Non-Expert Data to Robustify Imitation Learning via Offline Reinforcement Learning** [[paper](https://arxiv.org/abs/2510.19495)]
- [2025] **Guiding Energy-Efficient Locomotion through Impact Mitigation Rewards** [[paper](https://arxiv.org/abs/2510.09543)]
- [2025] **Improving the performance of AI-powered Affordable Robotics for Assistive Tasks** [[paper](https://arxiv.org/abs/2510.21771)]
- [2025] **RM-RL: Role-Model Reinforcement Learning for Precise Robot Manipulation** [[paper](https://arxiv.org/abs/2510.15189)]
- [2025] **SPACeR: Self-Play Anchoring with Centralized Reference Models** [[paper](https://arxiv.org/abs/2510.18060)]
- [2025] **RoDyn: Taming Interactive Robot-Dynamic 2.5D World Model for Robotic Manipulation** [[paper](https://arxiv.org/abs/2510.09036)]
- [2025] **CoIRL-AD: Collaborative-Competitive Imitation-Reinforcement Learning in Latent World Models for Autonomous Driving** [[paper](https://arxiv.org/abs/2510.12560)]
- [2025] **VLA-RFT: Vision-Language-Action Reinforcement Fine-tuning with Verified Rewards in World Simulators** [[paper](https://arxiv.org/abs/2510.00406)]
- [2025] **A Recipe for Efficient Sim-to-Real Transfer in Manipulation with Online Imitation-Pretrained World Models** [[paper](https://arxiv.org/abs/2510.02538)]
- [2025] **Zero-Human Demonstration End-to-end Autonomous Driving with Trajectory Scorer** [[paper](https://arxiv.org/abs/2510.24108)]
- [2025] **DemoHLM: From One Demonstration to Generalizable Humanoid Loco-Manipulation** [[paper](https://arxiv.org/abs/2510.11258)]
- [2025] **Learning Generalizable Visuomotor Policy through Dynamics-Alignment** [[paper](https://arxiv.org/abs/2510.27114)]
- [2025] **Contrastive Representation Regularization for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2510.01711)]
- [2025] **Bridging Embodiment Gaps: Deploying Vision-Language-Action Models on Soft Robots** [[paper](https://arxiv.org/abs/2510.17369)]
- [2025] **Humanoid Everyday: A Comprehensive Robotic Dataset for Open-World Humanoid Manipulation** [[paper](https://arxiv.org/abs/2510.08807)]
- [2025] **Population-Coded Spiking Neural Networks for High-Dimensional Robotic Control** [[paper](https://arxiv.org/abs/2510.10516)]
- [2025] **DexMan: Learning Bimanual Dexterous Manipulation from Human and Generated Videos** [[paper](https://arxiv.org/abs/2510.08475)]
- [2025] **Viability-Preserving Passive Torque Control** [[paper](https://arxiv.org/abs/2510.03367)]
- [2025] **RL-100: Performant Robotic Manipulation with Real-World Reinforcement Learning** [[paper](https://arxiv.org/abs/2510.14830)]
- [2025] **EmbodiSwap for Zero-Shot Robot Imitation Learning** [[paper](https://arxiv.org/abs/2510.03706)]
- [2025] **ROPES: Robotic Pose Estimation via Score-Based Causal Representation Learning** [[paper](https://arxiv.org/abs/2510.20884)]
- [2025] **Action Chunking with Transformers for Image-Based Spacecraft Guidance and Control** [[paper](https://arxiv.org/abs/2509.04628)]
- [2025] **World4RL: Diffusion World Models for Policy Refinement with Reinforcement Learning for Robotic Manipulation** [[paper](https://arxiv.org/abs/2509.19080)]
- [2025] **Learning-Based Planning for Improving Science Return of Earth Observation Satellites** [[paper](https://arxiv.org/abs/2509.07997)]
- [2025] **TreeIRL: Safe Urban Driving with Tree Search and Inverse Reinforcement Learning** [[paper](https://arxiv.org/abs/2509.13579)]
- [2025] **EigenSafe: A Spectral Framework for Learning-Based Probabilistic Safety Assessment** [[paper](https://arxiv.org/abs/2509.17750)]
- [2025] **World-Env: Leveraging World Model as a Virtual Environment for VLA Post-Training** [[paper](https://arxiv.org/abs/2509.24948)]
- [2025] **RoboManipBaselines: A Unified Framework for Imitation Learning in Robotic Manipulation across Real and Simulation Environments** [[paper](https://arxiv.org/abs/2509.17057)]
- [2025] **ViReSkill: Vision-Grounded Replanning with Skill Memory for LLM-Based Planning in Lifelong Robot Learning** [[paper](https://arxiv.org/abs/2509.24219)]
- [2025] **Ratatouille: Imitation Learning Ingredients for Real-world Social Robot Navigation** [[paper](https://arxiv.org/abs/2509.17204)]
- [2025] **Balancing Signal and Variance: Adaptive Offline RL Post-Training for VLA Flow Models** [[paper](https://arxiv.org/abs/2509.04063)]
- [2025] **PegasusFlow: Parallel Rolling-Denoising Score Sampling for Robot Diffusion Planner Flow Matching** [[paper](https://arxiv.org/abs/2509.08435)]
- [2025] **DexSkin: High-Coverage Conformable Robotic Skin for Learning Contact-Rich Manipulation** [[paper](https://arxiv.org/abs/2509.18830)]
- [2025] **The Role of Embodiment in Intuitive Whole-Body Teleoperation for Mobile Manipulation** [[paper](https://arxiv.org/abs/2509.03222)]
- [2025] **Bi-VLA: Bilateral Control-Based Imitation Learning via Vision-Language Fusion for Action Generation** [[paper](https://arxiv.org/abs/2509.18865)]
- [2025] **Learning Particle Dynamics Subject to Rigid Body Manipulations Using Graph Neural Networks** [[paper](https://arxiv.org/abs/2509.03446)]
- [2025] **The Role of Touch: Towards Optimal Tactile Sensing Distribution in Anthropomorphic Hands for Dexterous In-Hand Manipulation** [[paper](https://arxiv.org/abs/2509.14984)]
- [2025] **Learning Contact Dynamics through Touching: Action-conditional Graph Neural Networks for Robotic Peg Insertion** [[paper](https://arxiv.org/abs/2509.12151)]
- [2025] **Robotic Skill Diversification via Active Mutation of Reward Functions in Reinforcement Learning During a Liquid Pouring Task** [[paper](https://arxiv.org/abs/2509.18463)]
- [2025] **ImaginationPolicy: Towards Generalizable, Precise and Reliable End-to-End Policy for Robotic Manipulation** [[paper](https://arxiv.org/abs/2509.20841)]
- [2025] **From Code to Action: Hierarchical Learning of Diffusion-VLM Policies** [[paper](https://arxiv.org/abs/2509.24917)]
- [2025] **Learning Dolly-In Filming From Demonstration Using a Ground-Based Robot** [[paper](https://arxiv.org/abs/2509.00574)]
- [2025] **LodeStar: Long-horizon Dexterity via Synthetic Data Augmentation from Human Demonstrations** [[paper](https://arxiv.org/abs/2508.17547)]
- [2025] **Robotic Manipulation via Imitation Learning: Taxonomy, Evolution, Benchmark, and Challenges** [[paper](https://arxiv.org/abs/2508.17449)]
- [2025] **GWM: Towards Scalable Gaussian World Models for Robotic Manipulation** [[paper](https://arxiv.org/abs/2508.17600)]
- [2025] **A Vision-Based Shared-Control Teleoperation Scheme for Controlling the Robotic Arm of a Four-Legged Robot** [[paper](https://arxiv.org/abs/2508.14994)]
- [2025] **Exploiting Policy Idling for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2508.15669)]

[⬆ Back to top](#paper-list)

### Human-Robot Interaction

#### Theory

##### 2026

- [2026] **Guest editorial: The next wave of innovation. Human, enterprise, and artificial intelligence united for impactful change** *European Journal of Innovation Management* [[paper](https://doi.org/10.1108/ejim-08-2026-150)]
- [2026] **From testbeds to high-stakes work: a review of Human-AI teaming domains and teaming factors** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1733942)]
- [2026] **NEOMANITAI V7.1 Domain Term-Sets: 15 Fields of Human-AI and Robotics Interaction Phenomena (Restricted)** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20060992)]
- [2026] **Guest editorial: AI for a better future – advances, challenges and future research directions** *Internet Research* [[paper](https://doi.org/10.1108/intr-06-2026-034)]
- [2026] **From Fragmentation to Integration: Designing Humanoid Robots for Corporate Service Environments** *TUbilio (Technical University of Darmstadt)* [[paper](https://tubiblio.ulb.tu-darmstadt.de/view/person/Leichtle=3AMarcel=3A=3A.html>)]
- [2026] **Guest editorial: Digital innovation ecosystem: profiting from technology in the era of twin transition** *European Journal of Innovation Management* [[paper](https://doi.org/10.1108/ejim-02-2026-056)]
- [2026] **A Human-Centred Tri-Region Shared Autonomy Framework for Adaptive and Safe Human–Robot Interaction** [[paper](https://doi.org/10.1145/3776734.3794536)]
- [2026] **Agentic AI in services: orchestrating human–machine synergy for service excellence** *International Journal of Quality and Service Sciences* [[paper](https://doi.org/10.1108/ijqss-03-2026-303)]
- [2026] **Artificial intelligence and machine learning in assessing and promoting health and well‐being: Integrating human insight with computational intelligence** *Applied Psychology Health and Well-Being* [[paper](https://doi.org/10.1111/aphw.70140)]
- [2026] **Distributed control strategies for cooperative and collaborative object transportation via Multi-Robot systems** *CINECA IRIS Institutial Research Information System (University of Genoa)* [[paper](https://hdl.handle.net/11567/1288096)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **Feedback modalities in human-cobot collaboration: experimental evaluation of performance, user experience, and physiological responses** *Frontiers in Robotics and AI* [[paper](https://doi.org/10.3389/frobt.2026.1836165)]
- [2026] **AI-driven quadruped robots: from fundamental locomotion to advanced biomimetic behaviors** *Frontiers in Neurorobotics* [[paper](https://doi.org/10.3389/fnbot.2026.1855550)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Imitation learning for human–robot teaming in battery disassembly: enabling technologies and a collaborative manipulation pipeline** [[paper](https://doi.org/10.7148/2026-0161)]
- [2026] **Advancing Human-Robot Collaboration in Teleoperation: Comparative Evaluation of Shared Control Modalities Across Tasks and Interfaces** *International Journal of Human-Computer Interaction* [[paper](https://doi.org/10.1080/10447318.2026.2633203)]
- [2026] **Planning, Execution, to After-Action Review (PETAAR): A Toolset for Human-Robot Teaming** [[paper](https://doi.org/10.1145/3776734.3794389)]

[⬆ Back to top](#paper-list)

#### Application

##### 2026

- [2026] **Locomotion Variability and User Experience in Smart Wheelchair Human-Robot Interaction** [[paper](https://arxiv.org/abs/2608.11417)]
- [2026] **HRIBench: Benchmarking Interaction-Centric Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2607.13056)]
- [2026] **Environment Design for Reliable Shared Autonomy with Probabilistic Guarantees** [[paper](https://arxiv.org/abs/2607.15487)]
- [2026] **Not Forgotten: Implementation and Evaluation of a Personalized Episodic Memory for the Humanoid Robot Head Kim** [[paper](https://arxiv.org/abs/2607.24190)]
- [2026] **Corrigible Assistance in One Round: Pragmatic-Pedagogic Best Response** [[paper](https://arxiv.org/abs/2607.27508)]
- [2026] **Validating Virtual Reality for Studying Multimodal Human-Robot Interaction in Socially Aware Robot Navigation** [[paper](https://arxiv.org/abs/2607.09261)]
- [2026] **Toward Low-Latency Vision-Language Models with Doubly-Correct Predictions in Egocentric Visual Understanding** [[paper](https://arxiv.org/abs/2606.25160)]
- [2026] **Semantically-Aware Diver Activity Recognition Framework for Effective Underwater Multi-Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2606.12374)]
- [2026] **Legible Shared Autonomy: Implicit Communication of Robot Belief through Motion** [[paper](https://arxiv.org/abs/2606.29846)]
- [2026] **One Body, Two Minds: Variable Autonomy Approach for a Co-embodied Robotic Hand** [[paper](https://arxiv.org/abs/2606.25575)]
- [2026] **What Is My Robot Thinking? Design Considerations for Transparent and Trustworthy Shared Autonomy** [[paper](https://arxiv.org/abs/2606.06870)]
- [2026] **Charting the Growth of Social-Physical HRI (spHRI): A Systematic Review Pipeline Augmented by Small Language Models** [[paper](https://arxiv.org/abs/2606.26382)]
- [2026] **A Taxonomy of Conceptual Alignment in Human-Robot Dialogue** [[paper](https://arxiv.org/abs/2606.22360)]
- [2026] **HABIT: Human-Aware Behavior and Interaction Training Dataset for Robot Manipulation** [[paper](https://arxiv.org/abs/2606.31682)]
- [2026] **Simulation-Driven Imitation Learning for Biosignals-Free Shared-Autonomy Prosthetic Grasping** [[paper](https://arxiv.org/abs/2606.07389)]
- [2026] **SAPS: Shared Autonomy for Policy Steering by Blending Teleoperation with a Pretrained VLA** [[paper](https://arxiv.org/abs/2606.15568)]
- [2026] **Human-Guided Co-Manipulation of Carbon Fiber Plies** [[paper](https://arxiv.org/abs/2606.11818)]
- [2026] **Understanding and Modeling Perceived Cognitive and Physical Strain Dynamics for Planning-Oriented Human-Robot Collaboration in Prefabricated Construction** [[paper](https://arxiv.org/abs/2606.15494)]
- [2026] **Proximal State Nudging: Reducing Skill Atrophy from AI Assistance** [[paper](https://arxiv.org/abs/2605.20355)]
- [2026] **PACT: Proactive Asking for Continual Task Assistance in Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2605.24350)]
- [2026] **Adaptive Human-Robot Collaboration for Masonry Construction Under Material and Assembly Uncertainty** [[paper](https://arxiv.org/abs/2605.20264)]
- [2026] **AssistDLO: Assistive Teleoperation for Deformable Linear Object Manipulation** [[paper](https://arxiv.org/abs/2605.06323)]
- [2026] **Shared Autonomy Assisted by Impedance-Driven Anisotropic Guidance Field** [[paper](https://arxiv.org/abs/2605.02410)]
- [2026] **Exploring Human-Robot Collaboration: Analysis of Interaction Modalities in Challenging Tasks** [[paper](https://arxiv.org/abs/2605.13380)]
- [2026] **Tactile-Proprioceptive Sensor Fusion for Contact Wrench Estimation in Whole-Body Physical Human-Robot Interaction** [[paper](https://arxiv.org/abs/2605.28412)]
- [2026] **Precise Robot Command Understanding Using Grammar-Constrained Large Language Models** [[paper](https://arxiv.org/abs/2604.04233)]
- [2026] **Multimodal Anomaly Detection for Human-Robot Interaction** [[paper](https://arxiv.org/abs/2604.09326)]
- [2026] **Warmth and Competence in the Swarm: Designing Effective Human-Robot Teams** [[paper](https://arxiv.org/abs/2604.19270)]
- [2026] **Vision-Based Safe Human-Robot Collaboration with Uncertainty Guarantees** [[paper](https://arxiv.org/abs/2604.15221)]
- [2026] **A Unified Multi-Layer Framework for Skill Acquisition from Imperfect Human Demonstrations** [[paper](https://arxiv.org/abs/2604.08341)]
- [2026] **Joint Prediction of Human Motions and Actions in Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2604.03065)]
- [2026] **AURA: Multimodal Shared Autonomy for Real-World Urban Navigation** [[paper](https://arxiv.org/abs/2604.01659)]
- [2026] **Control Barrier Functions Solved with Hierarchical Quadratic Programming for Safe Physical Human-Robot Interaction** [[paper](https://arxiv.org/abs/2604.23039)]
- [2026] **LLM-Guided Safety Agent for Edge Robotics with an ISO-Compliant Perception-Compute-Control Architecture** [[paper](https://arxiv.org/abs/2604.20193)]
- [2026] **A Replicable Robotics Awareness Method Using LLM-Enabled Robotics Interaction: Evidence from a Corporate Challenge** [[paper](https://arxiv.org/abs/2604.21377)]
- [2026] **Intuitive Human-Robot Interaction: Development and Evaluation of a Gesture-Based User Interface for Object Selection** [[paper](https://arxiv.org/abs/2604.06073)]
- [2026] **SASI: Leveraging Sub-Action Semantics for Robust Early Action Recognition in Human-Robot Interaction** [[paper](https://arxiv.org/abs/2604.27508)]
- [2026] **SUBTA: A Framework for Supported User-Guided Bimanual Teleoperation in Structured Assembly** [[paper](https://arxiv.org/abs/2603.10459)]
- [2026] **TATIC: Task-Aware Temporal Learning for Human Intent Inference from Physical Corrections in Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2603.11077)]
- [2026] **Robotic Grasping and Placement Controlled by EEG-Based Hybrid Visual and Motor Imagery** [[paper](https://arxiv.org/abs/2603.03181)]
- [2026] **DiSCo: Diffusion Sequence Copilots for Shared Autonomy** [[paper](https://arxiv.org/abs/2603.22787)]
- [2026] **CoViLLM: An Adaptive Human-Robot Collaborative Assembly Framework Using Large Language Models** [[paper](https://arxiv.org/abs/2603.11461)]
- [2026] **A Safety-Aware Shared Autonomy Framework with BarrierIK Using Control Barrier Functions** [[paper](https://arxiv.org/abs/2603.01705)]
- [2026] **Decision-Aware Uncertainty Evaluation of Vision-Language Model-Based Early Action Anticipation for Human-Robot Interaction** [[paper](https://arxiv.org/abs/2603.10061)]
- [2026] **Age-Related Differences in the Perception of Eye-Gaze from a Social Robot** [[paper](https://arxiv.org/abs/2603.08810)]
- [2026] **Sense4HRI: A ROS 2 HRI Framework for Physiological Sensor Integration and Synchronized Logging** [[paper](https://arxiv.org/abs/2603.19914)]
- [2026] **Adaptive Vision-Based Control of Redundant Robots with Null-Space Interaction for Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2603.08089)]
- [2026] **SPIRIT: Perceptive Shared Autonomy for Robust Robotic Manipulation under Deep Learning Uncertainty** [[paper](https://arxiv.org/abs/2603.05111)]
- [2026] **Human-Aware Robot Behaviour in Self-Driving Labs** [[paper](https://arxiv.org/abs/2603.08420)]
- [2026] **An Approach to Combining Video and Speech with Large Language Models in Human-Robot Interaction** [[paper](https://arxiv.org/abs/2602.20219)]
- [2026] **Ontological grounding for sound and natural robot explanations via large language models** [[paper](https://arxiv.org/abs/2602.13800)]
- [2026] **Trust in Autonomous Human--Robot Collaboration: Effects of Responsive Interaction Policies** [[paper](https://arxiv.org/abs/2603.00154)]
- [2026] **Estimating Human Muscular Fatigue in Dynamic Collaborative Robotic Tasks with Learning-Based Models** [[paper](https://arxiv.org/abs/2602.15684)]
- [2026] **A Distributed Multi-Modal Sensing Approach for Human Activity Recognition in Real-Time Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2602.07024)]
- [2026] **Patch-Based Spatial Authorship Attribution in Human-Robot Collaborative Paintings** [[paper](https://arxiv.org/abs/2602.17030)]
- [2026] **6G Empowering Future Robotics: A Vision for Next-Generation Autonomous Systems** [[paper](https://arxiv.org/abs/2602.12246)]
- [2026] **End-to-end Optimization of Belief and Policy Learning in Shared Autonomy Paradigms** [[paper](https://arxiv.org/abs/2601.23285)]
- [2026] **Stochastic Decision-Making Framework for Human-Robot Collaboration in Industrial Applications** [[paper](https://arxiv.org/abs/2601.14809)]
- [2026] **EduSim-LLM: An Educational Platform Integrating Large Language Models and Robotic Simulation for Beginners** [[paper](https://arxiv.org/abs/2601.01196)]
- [2026] **From Perception to Symbolic Task Planning: Vision-Language Guided Human-Robot Collaborative Structured Assembly** [[paper](https://arxiv.org/abs/2601.00978)]
- [2026] **Explicit World Models for Reliable Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2601.01705)]
- [2026] **Estimating Trust in Human-Robot Collaboration through Behavioral Indicators and Explainability** [[paper](https://arxiv.org/abs/2601.19856)]

##### 2025

- [2025] **Breathe with Me: Synchronizing Biosignals for User Embodiment in Robots** [[paper](https://arxiv.org/abs/2512.14952)]
- [2025] **When Robots Say No: The Empathic Ethical Disobedience Benchmark** [[paper](https://arxiv.org/abs/2512.18474)]
- [2025] **LEO-RobotAgent: A General-purpose Robotic Agent for Language-driven Embodied Operator** [[paper](https://arxiv.org/abs/2512.10605)]
- [2025] **Real-Time Human-Robot Interaction Intent Detection Using RGB-based Pose and Emotion Cues with Cross-Camera Model Generalization** [[paper](https://arxiv.org/abs/2512.17958)]
- [2025] **Optimized Scheduling and Positioning of Mobile Manipulators in Collaborative Applications** [[paper](https://arxiv.org/abs/2512.17584)]
- [2025] **On Using Neural Networks to Learn Safety Speed Reduction in Human-Robot Collaboration: A Comparative Analysis** [[paper](https://arxiv.org/abs/2512.17579)]
- [2025] **A Hybrid Deep Learning Framework for Emotion Recognition in Children with Autism During NAO Robot-Mediated Interaction** [[paper](https://arxiv.org/abs/2512.12208)]
- [2025] **A Network-Based Framework for Modeling and Analyzing Human-Robot Coordination Strategies** [[paper](https://arxiv.org/abs/2512.15282)]
- [2025] **Robot Confirmation Generation and Action Planning Using Long-context Q-Former Integrated with Multimodal LLM** [[paper](https://arxiv.org/abs/2511.17335)]
- [2025] **Towards Affect-Adaptive Human-Robot Interaction: A Protocol for Multimodal Dataset Collection on Social Anxiety** [[paper](https://arxiv.org/abs/2511.13530)]
- [2025] **SAFe-Copilot: Unified Shared Autonomy Framework** [[paper](https://arxiv.org/abs/2511.04664)]
- [2025] **LAVQA: A Latency-Aware Visual Question Answering Framework for Shared Autonomy in Self-Driving Vehicles** [[paper](https://arxiv.org/abs/2511.11840)]
- [2025] **How Robot Kinematics Influence Human Performance in Virtual Robot-to-Human Handover Tasks** [[paper](https://arxiv.org/abs/2511.20299)]
- [2025] **A Shared Control Framework for Mobile Robots with Planning-Level Intention Prediction** [[paper](https://arxiv.org/abs/2511.08912)]
- [2025] **Towards Online Robot Interaction Adaptation to Human Upper-limb Mobility Impairments in Return-to-Work Scenarios** [[paper](https://arxiv.org/abs/2510.05425)]
- [2025] **Adaptive Motion Planning via Contact-Based Intent Inference for Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2510.08811)]
- [2025] **Design and Koopman Model Predictive Control of A Soft Exoskeleton Based on Origami-Inspired Pneumatic Actuator for Knee Rehabilitation** [[paper](https://arxiv.org/abs/2510.11094)]
- [2025] **AI-Enabled Capabilities to Facilitate Next-Generation Rover Surface Operations** [[paper](https://arxiv.org/abs/2510.05985)]
- [2025] **IntentionVLA: Generalizable and Efficient Embodied Intention Reasoning for Human-Robot Interaction** [[paper](https://arxiv.org/abs/2510.07778)]
- [2025] **Robotic Assistant: Completing Collaborative Tasks with Dexterous Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2510.25713)]
- [2025] **Investigating the Effect of LED Signals and Emotional Displays in Human-Robot Shared Workspaces** [[paper](https://arxiv.org/abs/2509.14748)]
- [2025] **Shared Autonomy through LLMs and Reinforcement Learning for Applications to Ship Hull Inspections** [[paper](https://arxiv.org/abs/2509.05042)]
- [2025] **Affordance-Based Disambiguation of Surgical Instructions for Collaborative Robot-Assisted Surgery** [[paper](https://arxiv.org/abs/2509.14967)]
- [2025] **Pointing-Guided Target Estimation via Transformer-Based Attention** [[paper](https://arxiv.org/abs/2509.05031)]
- [2025] **LiHRA: A LiDAR-Based HRI Dataset for Automated Risk Monitoring Methods** [[paper](https://arxiv.org/abs/2509.06597)]
- [2025] **TRUST 2025: SCRITA and RTSS @ RO-MAN 2025** [[paper](https://arxiv.org/abs/2509.11402)]
- [2025] **STL-Based Motion Planning and Uncertainty-Aware Risk Analysis for Human-Robot Collaboration with a Multi-Rotor Aerial Vehicle** [[paper](https://arxiv.org/abs/2509.10692)]
- [2025] **Knowledge Isn't Power: The Ethics of Social Robots and the Difficulty of Informed Consent** [[paper](https://arxiv.org/abs/2509.07942)]
- [2025] **The Influence of Facial Features on the Perceived Trustworthiness of a Social Robot** [[paper](https://arxiv.org/abs/2509.13948)]
- [2025] **Using Petri Nets for Context-Adaptive Robot Explanations** [[paper](https://arxiv.org/abs/2509.13861)]
- [2025] **Human Autonomy and Sense of Agency in Human-Robot Interaction: A Systematic Literature Review** [[paper](https://arxiv.org/abs/2509.22271)]
- [2025] **Teleoperator-Aware and Safety-Critical Adaptive Nonlinear MPC for Shared Autonomy in Obstacle Avoidance of Legged Robots** [[paper](https://arxiv.org/abs/2509.22815)]
- [2025] **EEG-Driven AR-Robot System for Zero-Touch Grasping Manipulation** [[paper](https://arxiv.org/abs/2509.20656)]
- [2025] **When and How to Express Empathy in Human-Robot Interaction Scenarios** [[paper](https://arxiv.org/abs/2509.25200)]
- [2025] **Safe Task Space Synchronization with Time-Delayed Information** [[paper](https://arxiv.org/abs/2509.22976)]

[⬆ Back to top](#paper-list)

### Multi-Robot Systems

#### Theory

##### 2026

- [2026] **Reinforcement-Guided Swarm Drones: Effects of PSO and Pheromones on Collective Behaviour** *Lecture notes in electrical engineering* [[paper](https://doi.org/10.1007/978-981-92-0779-4_13)]
- [2026] **MROPE: A Multi-Robot Safe Cooperative Strategy via combined Predictive Safety Filters and Ellipse-based Constraint Compression** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.29203)]
- [2026] **Collective Intelligence in Robotics: A Swarm Solution to Mapping and Payload Transport** *Research Square* [[paper](https://doi.org/10.21203/rs.3.rs-9794763/v1)]
- [2026] **Swarm AI Micro-Cockroach for Disaster Rescue** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20363989)]
- [2026] **Energy-Efficient Guided Deep Reinforcement Learning for Cooperative UAV Swarms** [[paper](https://doi.org/10.1109/iatmsi68868.2026.11465514)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **REAL TIME DECISION MAKING USING REINFORCEMENT LEARNING IN AUTONOMOUS ROBOTICS** [[paper](https://doi.org/10.71443/9789349552050-12)]
- [2026] **Swarm Robotics and Cooperative AI** *International Journal of Multidisciplinary Sciences and Technology* [[paper](https://doi.org/10.64137/31079911/ijmst-v2i1p103)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Multi-robot coordination and control frameworks for achieving resilient emergency management in hyperconnected and sensor-rich smart city environments** *IET conference proceedings.* [[paper](https://doi.org/10.1049/icp.2026.2564)]
- [2026] **A MODEL FOR SIMULATING RADIO-ELECTRONIC INTERFERENCE IN A DRONE SWARM SIMULATION ENVIRONMENT** [[paper](https://doi.org/10.70286/isu-01.07.2026.015)]
- [2026] **Adaptive Swarm Intelligence with Meta-Learning for Efficient Autonomous Multi-Robot Navigation and Pick-and-Drop Operations in Warehouse Environments** *International Journal of Novel Research and Development* [[paper](https://doi.org/10.56975/ijnrd.v11i5.325011)]
- [2026] **A Distributed Computer Vision System for Coordination Among Swarms OF Mobile Robots in Dynamic Warehouse Environments** *Neliti* [[paper](https://www.neliti.com/publications/712051/a-distributed-computer-vision-system-for-coordination-among-swarms-of-mobile-rob)]
- [2026] **Distributed Holographic Synchronization Algorithm for Cooperative Autonomous Underwater Exploration Robots** [[paper](https://doi.org/10.23919/indiacom70271.2026.11526696)]
- [2026] **SWARAM BOTS: AN ESP 32-BASED SWARAM ROBOTICS SYSTEM** *International Journal of Versatile Research and Analysis* [[paper](https://doi.org/10.56975/ijvra.v4i4.704045)]
- [2026] **HADEXION: Hadal Abyss Dynamics & Extreme-Pressure Intelligence** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.18883858)]
- [2026] **A Comprehensive Survey of Multi-Agent Reinforcement Learning for Autonomous Systems: Algorithms, Applications, and Open Challenges** *Research Square* [[paper](https://doi.org/10.21203/rs.3.rs-8751804/v1)]

[⬆ Back to top](#paper-list)

#### Development

##### 2026

- [2026] **Towards Intelligent UAV Path Planning: A Systematic Review of Hybrid Reinforcement Learning and Metaheuristic Optimization** *Research Square* [[paper](https://doi.org/10.21203/rs.3.rs-10315373/v1)]

[⬆ Back to top](#paper-list)

#### Systems & Technology

##### 2026

- [2026] **When Coordination Becomes a Threat: Communication Attacks in LLM-Controlled Multi-Robot Systems** [[paper](https://arxiv.org/abs/2608.06830)]
- [2026] **Learning-Based Motion Planning for Dynamic Environments: From Foundational Algorithms to Emerging Paradigms** [[paper](https://arxiv.org/abs/2608.00625)]
- [2026] **Complete, Scalable, and Robust Prioritized Planning for Multi-Robot Ordered Storage and Retrieval at Maximum Capacity** [[paper](https://arxiv.org/abs/2608.07734)]
- [2026] **A Forward-Inverse Dynamic Game Framework for Enhanced Multi-Agent Trajectory Planning** [[paper](https://arxiv.org/abs/2608.01636)]
- [2026] **When Prompts Control Robots: Prompt Injection Attacks in Multi-Agent Robotic Systems** [[paper](https://arxiv.org/abs/2608.00747)]
- [2026] **Unveiling Complex Collective Behaviors from Simple Rewards** [[paper](https://arxiv.org/abs/2607.12861)]
- [2026] **Anytime Plug-and-Play Control with Contract-Based Distributed MPC** [[paper](https://arxiv.org/abs/2607.04215)]
- [2026] **Embodied Human-Robot Interaction via Acoustics: A MARL Approach with AcoustoBots for Spatial Data Physicalization** [[paper](https://arxiv.org/abs/2607.06563)]
- [2026] **CILC: Cryptographically-secure Inter-agent Loop Closure Candidate Detection for Multi-Agent Collaborative SLAM** [[paper](https://arxiv.org/abs/2607.06700)]
- [2026] **CoDiMAD: Diffusion-Based Privileged Distillation for Communication-Free Multi-Robot Coordination** [[paper](https://arxiv.org/abs/2607.09587)]
- [2026] **SAGE: A Socially-Aware Generative Engine for Heterogeneous Multi-Agent Navigation** [[paper](https://arxiv.org/abs/2607.16619)]
- [2026] **When Multi-Robot Systems Meet Agentic AI:Towards Embodied Collective Intelligence** [[paper](https://arxiv.org/abs/2606.27929)]
- [2026] **Shape Formation for the Cooperative Transportation of Arbitrary Objects Using Multi-Agent Reinforcement Learning** [[paper](https://arxiv.org/abs/2606.09610)]
- [2026] **Formal Verification of Learned Multi-Agent Communication Policies via Decision Tree Distillation** [[paper](https://arxiv.org/abs/2606.19632)]
- [2026] **Sampling-Based Coordination-Informed Multi-Objective Multi-Robot Reinforcement Learning** [[paper](https://arxiv.org/abs/2606.30893)]
- [2026] **MASK: Multi-Agent Semantic K-Scheduling for Risk-Sensitive 6G Robotics** [[paper](https://arxiv.org/abs/2606.11249)]
- [2026] **Generative AI for Safe and Photorealistic Drone Light Shows** [[paper](https://arxiv.org/abs/2606.25458)]
- [2026] **Modular Reinforcement Learning For Cooperative Swarms** [[paper](https://arxiv.org/abs/2605.04939)]
- [2026] **Auction-Consensus Algorithm with Learned Bidding Scheme for Multi-Robot Systems** [[paper](https://arxiv.org/abs/2605.21932)]
- [2026] **PIMbot: A Self-Adaptive Attack Framework for Adversarial Manipulation of Multi-Robot Reinforcement Learning** [[paper](https://arxiv.org/abs/2605.23027)]
- [2026] **Generative Multi-Robot Motion Planning via Diffusion Modeling with Multi-Agent Reinforcement Learning Guidance** [[paper](https://arxiv.org/abs/2606.00933)]
- [2026] **Efficient Multi-Robot Motion Planning with Precomputed Translation-Invariant Edge Bundles** [[paper](https://arxiv.org/abs/2605.09801)]
- [2026] **Coordinating Task Switching in a Robotics Multi-Agent System Using Behavior Trees** [[paper](https://arxiv.org/abs/2606.01170)]
- [2026] **MAGS-SLAM: Monocular Multi-Agent Gaussian Splatting SLAM for Geometrically and Photometrically Consistent Reconstruction** [[paper](https://arxiv.org/abs/2605.10760)]
- [2026] **Many-to-Many Multi-Agent Pickup and Delivery** [[paper](https://arxiv.org/abs/2605.07835)]
- [2026] **Micro-Swarm Locomotion Optimization in Dynamic Flow using Multi-Objective Multi-Agent Reinforcement Learning** [[paper](https://arxiv.org/abs/2605.25025)]
- [2026] **Topology-Driven Anti-Entanglement Control for Soft Robots** [[paper](https://arxiv.org/abs/2605.05236)]
- [2026] **Crazyflow: An Accurate, GPU-Accelerated, Differentiable Drone Simulator in JAX** [[paper](https://arxiv.org/abs/2606.01478)]
- [2026] **CoMo3R-SLAM: Collaborative Monocular Dense SLAM with Learned 3D Reconstruction Priors for Outdoor Multi-Agent Systems** [[paper](https://arxiv.org/abs/2605.30488)]
- [2026] **Distributed Algorithm with Emergent Area Partitioning and Base Station's Situation Awareness for Multi-Robot Patrolling** [[paper](https://arxiv.org/abs/2605.01501)]
- [2026] **M2HRI: An LLM-Driven Multimodal Multi-Agent Framework for Personalized Human-Robot Interaction** [[paper](https://arxiv.org/abs/2604.11975)]
- [2026] **Federated Single-Agent Robotics: Multi-Robot Coordination Without Intra-Robot Multi-Agent Fragmentation** [[paper](https://arxiv.org/abs/2604.11028)]
- [2026] **Exploiting Aggregate Programming in a Multi-Robot Service Prototype** [[paper](https://arxiv.org/abs/2604.06876)]
- [2026] **Task-Driven Co-Design of Heterogeneous Multi-Robot Systems** [[paper](https://arxiv.org/abs/2604.21894)]
- [2026] **Cooperative Informative Sensing for Monitoring Dynamic Indoor Environments via Multi-Agent Reinforcement Learning** [[paper](https://arxiv.org/abs/2604.23179)]
- [2026] **Train-Small Deploy-Large: Leveraging Diffusion-Based Multi-Robot Planning** [[paper](https://arxiv.org/abs/2604.06598)]
- [2026] **Consent Chain Degradation in Embodied Multi-Agent Systems: Bridging the Gap Between AI Agent Governance and Robot Ethics** [[paper](https://arxiv.org/abs/2605.16300)]
- [2026] **Logical Robots: Declarative Multi-Agent Programming in Logica** [[paper](https://arxiv.org/abs/2604.06629)]
- [2026] **A Multimodal Framework for Human-Multi-Agent Interaction** [[paper](https://arxiv.org/abs/2603.23271)]
- [2026] **GRACE: A Unified 2D Multi-Robot Path Planning Simulator &amp; Benchmark for Grid, Roadmap, And Continuous Environments** [[paper](https://arxiv.org/abs/2603.10858)]
- [2026] **MA-VLCM: A Vision Language Critic Model for Value Estimation of Policies in Multi-Agent Team Settings** [[paper](https://arxiv.org/abs/2603.15418)]
- [2026] **Learning Visuomotor Policy for Multi-Robot Laser Tag Game** [[paper](https://arxiv.org/abs/2603.11980)]
- [2026] **Conflict Mitigation in Shared Environments using Flow-Aware Multi-Agent Path Finding** [[paper](https://arxiv.org/abs/2603.12736)]
- [2026] **DeReCo: Decoupling Representation and Coordination Learning for Object-Adaptive Decentralized Multi-Robot Cooperative Transport** [[paper](https://arxiv.org/abs/2603.08111)]
- [2026] **Scale-Plan: Scalable Language-Enabled Task Planning for Heterogeneous Multi-Robot Teams** [[paper](https://arxiv.org/abs/2603.08814)]
- [2026] **COHORT: Hybrid RL for Collaborative Large DNN Inference on Multi-Robot Systems Under Real-Time Constraints** [[paper](https://arxiv.org/abs/2603.10436)]
- [2026] **CREST: Constraint-Release Execution for Multi-Robot Warehouse Shelf Rearrangement** [[paper](https://arxiv.org/abs/2603.28803)]
- [2026] **A Classification of Heterogeneity in Uncrewed Vehicle Swarms and the Effects of Its Inclusion on Overall Swarm Resilience** [[paper](https://arxiv.org/abs/2603.28831)]
- [2026] **Large Neighborhood Search for Multi-Agent Task Assignment and Path Finding with Precedence Constraints** [[paper](https://arxiv.org/abs/2603.28968)]
- [2026] **Multi-Agent Off-World Exploration for Sparse Evidence Discovery via Gaussian Belief Mapping and Dual-Domain Coverage** [[paper](https://arxiv.org/abs/2603.07650)]
- [2026] **STL-SVPIO: Signal Temporal Logic guided Stein Variational Path Integral Optimization** [[paper](https://arxiv.org/abs/2603.13333)]
- [2026] **GoalSwarm: Multi-UAV Semantic Coordination for Open-Vocabulary Object Navigation** [[paper](https://arxiv.org/abs/2603.12908)]
- [2026] **S2Act: Simple Spiking Actor** [[paper](https://arxiv.org/abs/2603.15725)]
- [2026] **Ego to World: Collaborative Spatial Reasoning in Embodied Systems via Reinforcement Learning** [[paper](https://arxiv.org/abs/2603.14811)]
- [2026] **Scalable Multi-Robot Path Planning via Quadratic Unconstrained Binary Optimization** [[paper](https://arxiv.org/abs/2602.14799)]
- [2026] **Bandwidth-Efficient Multi-Agent Communication through Information Bottleneck and Vector Quantization** [[paper](https://arxiv.org/abs/2602.02035)]
- [2026] **Hierarchical LLM-Based Multi-Agent Framework with Prompt Optimization for Multi-Robot Task Planning** [[paper](https://arxiv.org/abs/2602.21670)]
- [2026] **Efficiently Solving Mixed-Hierarchy Games with Quasi-Policy Approximations** [[paper](https://arxiv.org/abs/2602.01568)]
- [2026] **CoLF: Learning Consistent Leader-Follower Policies for Vision-Language-Guided Multi-Robot Cooperative Transport** [[paper](https://arxiv.org/abs/2602.07776)]
- [2026] **AgentRob: From Virtual Forum Agents to Hijacked Physical Robots** [[paper](https://arxiv.org/abs/2602.13591)]
- [2026] **Hilbert-Augmented Reinforcement Learning for Scalable Multi-Robot Coverage and Exploration** [[paper](https://arxiv.org/abs/2602.19400)]
- [2026] **ActionReasoning: Robot Action Reasoning in 3D Space with LLM for Robotic Brick Stacking** [[paper](https://arxiv.org/abs/2602.21161)]
- [2026] **FISC: A Fluid-Inspired Framework for Decentralized and Scalable Swarm Control** [[paper](https://arxiv.org/abs/2602.00480)]
- [2026] **Judgelight: Trajectory-Level Post-Optimization for Multi-Agent Path Finding via Closed-Subwalk Collapsing** [[paper](https://arxiv.org/abs/2601.19388)]
- [2026] **AI-Augmented Density-Driven Optimal Control (D2OC) for Decentralized Environmental Mapping** [[paper](https://arxiv.org/abs/2601.21126)]
- [2026] **Advances and Innovations in the Multi-Agent Robotic System (MARS) Challenge** [[paper](https://arxiv.org/abs/2601.18733)]
- [2026] **Beyond Static Instruction: A Multi-agent AI Framework for Adaptive Augmented Reality Robot Training** [[paper](https://arxiv.org/abs/2603.00016)]

##### 2025

- [2025] **db-LaCAM: Fast and Scalable Multi-Robot Kinodynamic Motion Planning with Discontinuity-Bounded Search and Lightweight MAPF** [[paper](https://arxiv.org/abs/2512.06796)]
- [2025] **Mr. Virgil: Learning Multi-robot Visual-range Relative Localization** [[paper](https://arxiv.org/abs/2512.10540)]
- [2025] **Generalizable Collaborative Search-and-Capture in Cluttered Environments via Path-Guided MAPPO and Directional Frontier Allocation** [[paper](https://arxiv.org/abs/2512.09410)]
- [2025] **Robust Geospatial Coordination of Multi-Agent Communications Networks Under Attrition** [[paper](https://arxiv.org/abs/2512.02079)]
- [2025] **A Survey on Improving Human Robot Collaboration through Vision-and-Language Navigation** [[paper](https://arxiv.org/abs/2512.00027)]
- [2025] **An Analysis of Constraint-Based Multi-Agent Pathfinding Algorithms** [[paper](https://arxiv.org/abs/2511.18604)]
- [2025] **Collaborative Multi-Robot Non-Prehensile Manipulation via Flow-Matching Co-Generation** [[paper](https://arxiv.org/abs/2511.10874)]
- [2025] **Modelling and Model-Checking a ROS2 Multi-Robot System using Timed Rebeca** [[paper](https://arxiv.org/abs/2511.15227)]
- [2025] **Deadlock-Free Hybrid RL-MAPF Framework for Zero-Shot Multi-Robot Navigation** [[paper](https://arxiv.org/abs/2511.22685)]
- [2025] **MARS: Multi-Agent Robotic System with Multimodal Large Language Models for Assistive Intelligence** [[paper](https://arxiv.org/abs/2511.01594)]
- [2025] **Transforming Monolithic Foundation Models into Embodied Multi-Agent Architectures for Human-Robot Collaboration** [[paper](https://arxiv.org/abs/2512.00797)]
- [2025] **R2BC: Multi-Agent Imitation Learning from Single-Agent Demonstrations** [[paper](https://arxiv.org/abs/2510.18085)]
- [2025] **Zero-Shot Coordination in Ad Hoc Teams with Generalized Policy Improvement and Difference Rewards** [[paper](https://arxiv.org/abs/2510.16187)]
- [2025] **RoboOS-NeXT: A Unified Memory-based Framework for Lifelong, Scalable, and Robust Multi-Robot Collaboration** [[paper](https://arxiv.org/abs/2510.26536)]
- [2025] **Physics-Informed Neural Controlled Differential Equations for Scalable Long Horizon Multi-Agent Motion Forecasting** [[paper](https://arxiv.org/abs/2510.00401)]
- [2025] **Policies over Poses: Reinforcement Learning based Distributed Pose-Graph Optimization for Multi-Robot SLAM** [[paper](https://arxiv.org/abs/2510.22740)]
- [2025] **Have We Scene It All? Scene Graph-Aware Deep Point Cloud Compression** [[paper](https://arxiv.org/abs/2510.08512)]
- [2025] **Symmetry-Guided Multi-Agent Inverse Reinforcement Learning** [[paper](https://arxiv.org/abs/2509.08257)]
- [2025] **UDON: Uncertainty-weighted Distributed Optimization for Multi-Robot Neural Implicit Mapping under Extreme Communication Constraints** [[paper](https://arxiv.org/abs/2509.12702)]
- [2025] **CRAFT: Coaching Reinforcement Learning Autonomously using Foundation Models for Multi-Robot Coordination Tasks** [[paper](https://arxiv.org/abs/2509.14380)]
- [2025] **Policy Gradient with Self-Attention for Model-Free Distributed Nonlinear Multi-Agent Games** [[paper](https://arxiv.org/abs/2509.18371)]
- [2025] **Scalable Multi Agent Diffusion Policies for Coverage Control** [[paper](https://arxiv.org/abs/2509.17244)]
- [2025] **ELHPlan: Efficient Long-Horizon Task Planning for Multi-Agent Collaboration** [[paper](https://arxiv.org/abs/2509.24230)]
- [2025] **Beyond Detection -- Orchestrating Human-Robot-Robot Assistance via an Internet of Robotic Things Paradigm** [[paper](https://arxiv.org/abs/2509.22296)]
- [2025] **MAST: Multi-Agent Spatial Transformer for Learning to Collaborate** [[paper](https://arxiv.org/abs/2509.17195)]
- [2025] **Autonomous Multi-Robot Infrastructure for AI-Enabled Healthcare Delivery and Diagnostics** [[paper](https://arxiv.org/abs/2509.26106)]
- [2025] **MIMIC-D: Multi-modal Imitation for MultI-agent Coordination with Decentralized Diffusion Policies** [[paper](https://arxiv.org/abs/2509.14159)]
- [2025] **Discrete-Guided Diffusion for Scalable and Safe Multi-Robot Motion Planning** [[paper](https://arxiv.org/abs/2508.20095)]
- [2025] **DANCeRS: A Distributed Algorithm for Negotiating Consensus in Robot Swarms with Gaussian Belief Propagation** [[paper](https://arxiv.org/abs/2508.18153)]
- [2025] **Virtual Community: An Open World for Humans, Robots, and Society** [[paper](https://arxiv.org/abs/2508.14893)]

[⬆ Back to top](#paper-list)

### Simulation & World Models

#### Theory

##### 2026

- [2026] **CAA-X V5.1 Robot Extension (CAA-R): Modular Control for Embodied Agents — Revised and Expanded Edition** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.21896904)]
- [2026] **SIMULATION ENVIRONMENTS FOR TRAINING REINFORCEMENT LEARNING DRIVEN ROBOTIC SYSTEMS** [[paper](https://doi.org/10.71443/9789349552050-09)]
- [2026] **Physical AI: The Convergence of Foundation Models, Sim-to-Real Transfer, and Embodied Intelligence** *Journal of Multimedia Information System* [[paper](https://doi.org/10.33851/jmis.2026.13.2.53)]
- [2026] **Closing the Sim-to-Real Loop Through Representation, Interface, and Feedback: How Dynamics-Aware Perception, Factored Policy Structure, and Embodied Feedback Jointly Determine Transfer Fidelity in Robot Learning** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20642294)]
- [2026] **Embodied Deployment Constraints as a Design Variable: How Edge Inference Budgets, Tactile Representation, Temporal Decoupling, Credit Assignment, and Safety Certification Jointly Constrain Real-World Robot Policy Deployment** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20731139)]
- [2026] **Physical AI: The Next Frontier in AI and Robotics to Build Truly Autonomous Machines** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202604.0549.v1)]
- [2026] **Evolutionary Optimization for Tuning Robot Swarms in Coverage Problems** *Open MIND* [[paper](https://doi.org/10.26190/unsworks/32094)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **Time-to-Collision Based Dynamic Obstacle Avoidance Using Pretrained Vision Models for Robots in Unstructured Environments** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.07885)]
- [2026] **REALITY STRIKES BACK: A CONCEPT-CENTRIC FRAMEWORK FOR ADDRESSING THE SIM-TO-REAL GAP IN MANUFACTURING SIMULATION** *OSF Preprints (OSF Preprints)* [[paper](https://osf.io/86cgu)]
- [2026] **Sim-to-Real Transfer of Vision-Language Navigation in Continuous Environments Using an Ackermann-Steered Mobile Robot** [[paper](https://doi.org/10.1109/iccar69571.2026.11549553)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Bridging the Sim-to-Real Gap in Parallel-Link Leg Mechanisms via Simulator-Side Dynamics Normalization** [[paper](https://arxiv.org/abs/2608.01697)]
- [2026] **LyEvO: Lyapunov-Guided Evolutionary Optimization for Safe and Robust Sim-to-Real Policy Learning** [[paper](https://arxiv.org/abs/2608.06481)]
- [2026] **Autonomous sailing with sim-to-real reinforcement learning** *Engineering Applications of Artificial Intelligence* [[paper](https://doi.org/10.1016/j.engappai.2026.115804)]
- [2026] **A Capacitive Tactile Sensor Digital Twin for Real-Time Synthetic Data Generation and Sim-to-Real Transfer in NVIDIA Isaac Sim** *Applied Sciences* [[paper](https://doi.org/10.3390/app16157708)]
- [2026] **Bridging the Simulation-to-Reality Gap in Reinforcement Learning-Based Autonomous Robot Navigation** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.21791119)]
- [2026] **BIFROST: Bridging Invariant Feature Representation for Observation-space Sim2Real Transfer** [[paper](https://arxiv.org/abs/2607.01410)]
- [2026] **Efficient Transfer Learning of Robot Dynamic Models Using Morphological Similarity** [[paper](https://arxiv.org/abs/2607.05665)]
- [2026] **Difference-Based Relational Learning for Zero-Shot Object-Goal Visual Navigation With Direct Sim-to-Real Transfer** [[paper](https://arxiv.org/abs/2607.15642)]
- [2026] **A Cyclic Adaptation-Generalization Framework with Uncertainty-Guided Self-Paced Learning for Long-Term Brain-Machine Interfaces** [[paper](https://arxiv.org/abs/2607.24031)]
- [2026] **Bridging the Sim-to-Real Gap under Real-Time Constraints in Autonomous Racing** [[paper](https://arxiv.org/abs/2607.18586)]
- [2026] **Effective Parameters, Real Behavior: Renormalization for Robotics -- From Infinite Electron Mass to Sim-to-Real Gap** [[paper](https://arxiv.org/abs/2607.24079)]
- [2026] **Actuator Reality Shaping for Zero-Shot Sim-to-Real Robot Learning** [[paper](https://arxiv.org/abs/2607.02205)]
- [2026] **Towards bridging the gap: Systematic sim-to-real transfer for diverse legged robots** *The International Journal of Robotics Research* [[paper](https://arxiv.org/abs/2509.06342)]
- [2026] **Scaling Sim-to-Real Learning for Robot Manipulation** *KiltHub Repository* [[paper](https://doi.org/10.1184/r1/32984711.v1)]
- [2026] **World Translation: Minimizing Sim-to-Real Gap with Backward Dynamics Extraction and Unpaired Domain Translation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.18154)]
- [2026] **Vision-Language-Action Models for Embodied AI: A Survey of Robotics, Manipulation, and Autonomous Agents** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.21366292)]
- [2026] **State of World Models 2026 : Taxonomy, Benchmarks and Open Challenges** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.21345187)]
- [2026] **Efficient Sim-to-Real Transfer of World-Action Models from Synthetic Priors** [[paper](https://arxiv.org/abs/2606.31101)]
- [2026] **FADA: Few-Shot Domain Adaptation via Dynamics Alignment for Humanoid Control** [[paper](https://arxiv.org/abs/2606.28476)]
- [2026] **A Scalable Embodied Intelligence Platform for Seamless Real-to-Sim-to-Real Transfer of Household Mobile Manipulation Tasks** [[paper](https://arxiv.org/abs/2606.18646)]
- [2026] **Benchmarking Action Spaces in Reinforcement Learning for Vision-based Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.18594)]
- [2026] **Bridging the sim2real gap in the table tennis robot with a transformer-based ball states predictor** [[paper](https://arxiv.org/abs/2606.11464)]
- [2026] **Robotic Policy Adaptation via Weight-Space Meta-Learning** [[paper](https://arxiv.org/abs/2606.07217)]
- [2026] **SimWeaver: Zero-Shot RGB Sim-to-Real for Deformable Manipulation** [[paper](https://arxiv.org/abs/2606.15338)]
- [2026] **ConCent: Contact-Centric Real-to-Sim-to-Real Learning from One Demonstration** [[paper](https://arxiv.org/abs/2606.30268)]
- [2026] **FalconTrack: Photorealistic Auto-Labeled Perception and Physics-Aware Vision-Based Aerial Tracking** [[paper](https://arxiv.org/abs/2606.29783)]
- [2026] **CORE Planner: Contextual-memory Oriented Reinforcement-learning in Unknown Environments for Robot Navigation** [[paper](https://arxiv.org/abs/2606.29222)]
- [2026] **Video2Sim2Real: Full-Stack Autonomous Dexterous Skill Acquisition from a Single Human Video** [[paper](https://arxiv.org/abs/2606.08828)]
- [2026] **Physics Models for Sim-to-Real Transfer in Professional-Level Robot Table Tennis** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.28805)]
- [2026] **TactSpace: Learning a Physics-enriched Shared Latent Space for Tactile Sim-to-Real Transfer** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.18959)]
- [2026] **VIRTUS-FPP: Virtual Sensor Modeling for Fringe Projection Profilometry in NVIDIA Isaac Sim** *IEEE Sensors Journal* [[paper](https://arxiv.org/abs/2509.22685)]
- [2026] **AirDreamer: Generalist Drone Navigation with World Models** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.03252)]
- [2026] **DeformX: A Versatile Co-Simulation Framework for Deformable Linear Objects** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.22116)]
- [2026] **TacCoRL: Integrating Tactile Feedback into VLA via Simulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.11743)]
- [2026] **Construction of an industrial digital twin platform for multi-robot arm collaborative control** *DOAJ (DOAJ: Directory of Open Access Journals)* [[paper](https://doaj.org/article/e06a7777def141b3b6714e34080ea715)]
- [2026] **Real-Time Whole-Body Teleoperation of a Humanoid Robot Using IMU-Based Motion Capture with Sim2Sim and Sim2Real Validation** [[paper](https://arxiv.org/abs/2605.12347)]
- [2026] **Too Much of a Good Thing: When sim2real Efforts Impede Policy Learning (And What to Do About It)** [[paper](https://arxiv.org/abs/2606.02636)]
- [2026] **VLA-REPLICA: A Low-Cost, Reproducible Benchmark for Real-World Evaluation of Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2605.20774)]
- [2026] **Beyond Binary: Sim-to-Real Dexterous Manipulation with Physics-Grounded Contact Representation** [[paper](https://arxiv.org/abs/2605.28812)]
- [2026] **DexSim2Real: Foundation Model-Guided Sim-to-Real Transfer for Generalizable Dexterous Manipulation** [[paper](https://arxiv.org/abs/2605.05241)]
- [2026] **HyperSim: A Holistic Sim-To-Real Framework For Robust Robotic Manipulation** [[paper](https://arxiv.org/abs/2605.26638)]
- [2026] **REAP: Reinforcement-Learning End-to-End Autonomous Parking with Gaussian Splatting Simulator for Real2Sim2Real Transfer** [[paper](https://arxiv.org/abs/2605.08713)]
- [2026] **NavRL++: A System-Level Framework for Improving Sim-to-Real Transfer in Reinforcement Learning-Based Robot Navigation** [[paper](https://arxiv.org/abs/2605.15559)]
- [2026] **Closed-Loop Sim-to-Real Reinforcement Learning for Deformable Microfiber Shape Control** [[paper](https://arxiv.org/abs/2605.21688)]
- [2026] **Anatomical Landmark-Guided Deep Reinforcement Learning for Autonomous Gastric Navigation** [[paper](https://arxiv.org/abs/2605.08269)]
- [2026] **DRL-Based Pose Control for Double-Ackermann Robots Under Actuation Uncertainties** *HAL (Le Centre pour la Communication Scientifique Directe)* [[paper](https://arxiv.org/abs/2606.00313)]
- [2026] **3D Generation for Embodied AI and Robotic Simulation: A Survey** [[paper](https://arxiv.org/abs/2604.26509)]
- [2026] **Abstract Sim2Real through Approximate Information States** [[paper](https://arxiv.org/abs/2604.15289)]
- [2026] **Sim2Real-AD: A Modular Sim-to-Real Framework for Deploying VLM-Guided Reinforcement Learning in Real-World Autonomous Driving** [[paper](https://arxiv.org/abs/2604.03497)]
- [2026] **GaussFly: Contrastive Reinforcement Learning for Visuomotor Policies in 3D Gaussian Fields** [[paper](https://arxiv.org/abs/2604.05062)]
- [2026] **Generative Simulation for Policy Learning in Physical Human-Robot Interaction** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.08664)]
- [2026] **AI and mechanics driving the rise of bio-inspired robotic swarms** [[paper](https://doi.org/10.1117/12.3089992)]
- [2026] **DexWorldModel: Causal Latent World Modeling towards Automated Learning of Embodied Tasks** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2604.16484)]
- [2026] **DRUM: Diffusion-based Raydrop-aware Unpaired Mapping for Sim2Real LiDAR Segmentation** [[paper](https://arxiv.org/abs/2603.26263)]
- [2026] **CataractSAM-2: A Domain-Adapted Model for Anterior Segment Surgery Segmentation and Scalable Ground-Truth Annotation** [[paper](https://arxiv.org/abs/2603.21566)]
- [2026] **Robust Sim-to-Real Cloth Untangling through Reduced-Resolution Observations via Adaptive Force-Difference Quantization** [[paper](https://arxiv.org/abs/2603.13785)]
- [2026] **Neural Aided Adaptive Innovation-Based Invariant Kalman Filter** [[paper](https://arxiv.org/abs/2603.26709)]
- [2026] **Sim2Sea: Sim-to-Real Policy Transfer for Maritime Vessel Navigation in Congested Waters** [[paper](https://arxiv.org/abs/2603.04057)]
- [2026] **Grounding Sim-to-Real Generalization in Robotic Manipulation: An Empirical Study with Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2603.22876)]
- [2026] **AGILE: A Comprehensive Workflow for Humanoid Loco-Manipulation Learning** [[paper](https://arxiv.org/abs/2603.20147)]
- [2026] **Scaling Sim-to-Real Reinforcement Learning for Robot VLAs with Generative 3D Worlds** [[paper](https://arxiv.org/abs/2603.18532)]
- [2026] **Tendon Force Modeling for Sim2Real Transfer of Reinforcement Learning Policies for Tendon-Driven Robots** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.04351)]
- [2026] **ExpertGen: Scalable Sim-to-Real Expert Policy Learning from Imperfect Behavior Priors** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.15956)]
- [2026] **V-Dreamer: Automating Robotic Simulation and Trajectory Synthesis via Video Generation Priors** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.18811)]
- [2026] **TactGen: Tactile Sensory Data Generation via Zero-Shot Sim-to-Real Transfer (Abstract Reprint)** *Proceedings of the AAAI Conference on Artificial Intelligence* [[paper](https://doi.org/10.1609/aaai.v40i47.41424)]
- [2026] **Cooperative-Competitive Team Play of Real-World Craft Robots** [[paper](https://arxiv.org/abs/2602.21119)]
- [2026] **Instance-Guided Unsupervised Domain Adaptation for Robotic Semantic Segmentation** [[paper](https://arxiv.org/abs/2602.01389)]
- [2026] **Bridging the Sim-to-Real Gap with multipanda ros2: A Real-Time ROS2 Framework for Multimanual Systems** [[paper](https://arxiv.org/abs/2602.02269)]
- [2026] **GeCo-SRT: Geometry-aware Continual Adaptation for Robotic Cross-Task Sim-to-Real Transfer** [[paper](https://arxiv.org/abs/2602.20871)]
- [2026] **Learning Agile Quadrotor Flight in the Real World** [[paper](https://arxiv.org/abs/2602.10111)]
- [2026] **ReaDy-Go: Real-to-Sim Dynamic 3D Gaussian Splatting Simulation for Environment-Specific Visual Navigation with Moving Obstacles** [[paper](https://arxiv.org/abs/2602.11575)]
- [2026] **SPARR: Simulation-based Policies with Asymmetric Real-world Residuals for Assembly** [[paper](https://arxiv.org/abs/2602.23253)]
- [2026] **HydroShear: Hydroelastic Shear Simulation for Tactile Sim-to-Real Reinforcement Learning** [[paper](https://arxiv.org/abs/2603.00446)]
- [2026] **CLASH: Collision Learning via Augmented Sim-to-real Hybridization to Bridge the Reality Gap** [[paper](https://arxiv.org/abs/2602.18707)]
- [2026] **Learning Soccer Skills for Humanoid Robots: A Progressive Perception-Action Framework** [[paper](https://arxiv.org/abs/2602.05310)]
- [2026] **A High-Fidelity Digital Twin Framework for Multi-Modal Sim-to-Real Transfer for Robust UAV Autonomy** [[paper](https://doi.org/10.1109/i5cps67958.2026.11452535)]
- [2026] **Sim-to-Real Transfer via a Style-Identified Cycle Consistent Generative Adversarial Network: Zero-Shot Deployment on Robotic Manipulators through Visual Domain Adaptation** [[paper](https://arxiv.org/abs/2601.16677)]
- [2026] **CLAP: Contrastive Latent Action Pretraining for Learning Vision-Language-Action Models from Human Videos** [[paper](https://arxiv.org/abs/2601.04061)]
- [2026] **Sim2real Image Translation Enables Viewpoint-Robust Policies from Fixed-Camera Datasets** [[paper](https://arxiv.org/abs/2601.09605)]
- [2026] **Zero-Shot MARL Benchmark in the Cyber-Physical Mobility Lab** [[paper](https://arxiv.org/abs/2601.16578)]
- [2026] **Contact-Aware Neural Dynamics** [[paper](https://arxiv.org/abs/2601.12796)]
- [2026] **ExoGS: A 4D Real-to-Sim-to-Real Framework for Scalable Manipulation Data Collection** [[paper](https://arxiv.org/abs/2601.18629)]
- [2026] **Point Bridge: 3D Representations for Cross Domain Policy Learning** [[paper](https://arxiv.org/abs/2601.16212)]
- [2026] **HMVLA: Hyperbolic Multimodal Fusion for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2602.02533)]

##### 2025

- [2025] **Flying in Clutter on Monocular RGB by Learning in 3D Radiance Fields with Domain Adaptation** [[paper](https://arxiv.org/abs/2512.17349)]
- [2025] **INDOOR-LiDAR: Bridging Simulation and Reality for Robot-Centric 360 degree Indoor LiDAR Perception -- A Robot-Centric Hybrid Dataset** [[paper](https://arxiv.org/abs/2512.12377)]
- [2025] **CAHC:A General Conflict-Aware Heuristic Caching Framework for Multi-Agent Path Finding** [[paper](https://arxiv.org/abs/2512.12243)]
- [2025] **Learning Dexterous Manipulation Skills from Imperfect Simulations** [[paper](https://arxiv.org/abs/2512.02011)]
- [2025] **sim2art: Accurate Articulated Object Modeling from a Single Video using Synthetic Training Data Only** [[paper](https://arxiv.org/abs/2512.07698)]
- [2025] **Crossing the Sim2Real Gap Between Simulation and Ground Testing to Space Deployment of Autonomous Free-flyer Control** [[paper](https://arxiv.org/abs/2512.03736)]
- [2025] **RealD2iff: Bridging Real-World Gap in Robot Manipulation via Depth Diffusion** [[paper](https://arxiv.org/abs/2511.22505)]
- [2025] **DiffuDepGrasp: Diffusion-based Depth Noise Modeling Empowers Sim2Real Robotic Grasping** [[paper](https://arxiv.org/abs/2511.12912)]
- [2025] **Sim-to-Real Transfer in Deep Reinforcement Learning for Bipedal Locomotion** [[paper](https://arxiv.org/abs/2511.06465)]
- [2025] **Opening the Sim-to-Real Door for Humanoid Pixel-to-Action Policy Transfer** [[paper](https://arxiv.org/abs/2512.01061)]
- [2025] **Can Context Bridge the Reality Gap? Sim-to-Real Transfer of Context-Aware Policies** [[paper](https://arxiv.org/abs/2511.04249)]
- [2025] **MATrack: Efficient Multiscale Adaptive Tracker for Real-Time Nighttime UAV Operations** [[paper](https://arxiv.org/abs/2510.21586)]
- [2025] **GSWorld: Closed-Loop Photo-Realistic Simulation Suite for Robotic Manipulation** [[paper](https://arxiv.org/abs/2510.20813)]
- [2025] **Performance-guided Task-specific Optimization for Multirotor Design** [[paper](https://arxiv.org/abs/2510.04724)]
- [2025] **The Reality Gap in Robotics: Challenges, Solutions, and Best Practices** [[paper](https://arxiv.org/abs/2510.20808)]
- [2025] **A Survey on Collaborative SLAM with 3D Gaussian Splatting** [[paper](https://arxiv.org/abs/2510.23988)]
- [2025] **Towards Quadrupedal Jumping and Walking for Dynamic Locomotion using Reinforcement Learning** [[paper](https://arxiv.org/abs/2510.24584)]
- [2025] **ImMimic: Cross-Domain Imitation from Human Videos via Mapping and Interpolation** [[paper](https://arxiv.org/abs/2509.10952)]
- [2025] **EgoBridge: Domain Adaptation for Generalizable Imitation from Egocentric Human Data** [[paper](https://arxiv.org/abs/2509.19626)]
- [2025] **Sym2Real: Symbolic Dynamics with Residual Learning for Data-Efficient Adaptive Control** [[paper](https://arxiv.org/abs/2509.15412)]
- [2025] **Preventing Robotic Jailbreaking via Multimodal Domain Adaptation** [[paper](https://arxiv.org/abs/2509.23281)]
- [2025] **Deceptive Risk Minimization: Out-of-Distribution Generalization by Deceiving Distribution Shift Detectors** [[paper](https://arxiv.org/abs/2509.12081)]
- [2025] **Track Any Motions under Any Disturbances** [[paper](https://arxiv.org/abs/2509.13833)]
- [2025] **SPiDR: A Simple Approach for Zero-Shot Safety in Sim-to-Real Transfer** [[paper](https://arxiv.org/abs/2509.18648)]
- [2025] **Dynamic Adaptive Legged Locomotion Policy via Decoupling Reaction Force Control and Gait Control** [[paper](https://arxiv.org/abs/2509.13737)]
- [2025] **Best of Sim and Real: Decoupled Visuomotor Manipulation via Learning Control in Simulation and Perception in Real** [[paper](https://arxiv.org/abs/2509.25747)]
- [2025] **Synthetic vs. Real Training Data for Visual Navigation** [[paper](https://arxiv.org/abs/2509.11791)]
- [2025] **In-Hand Manipulation of Articulated Tools with Dexterous Robot Hands with Sim-to-Real Transfer** [[paper](https://arxiv.org/abs/2509.23075)]
- [2025] **Multi-Quadruped Cooperative Object Transport: Learning Decentralized Pinch-Lift-Move** [[paper](https://arxiv.org/abs/2509.14342)]
- [2025] **EmbodiedSplat: Personalized Real-to-Sim-to-Real Navigation with Gaussian Splats from a Mobile Device** [[paper](https://arxiv.org/abs/2509.17430)]
- [2025] **RealMirror: A Comprehensive, Open-Source Vision-Language-Action Platform for Embodied AI** [[paper](https://arxiv.org/abs/2509.14687)]
- [2025] **HERMES: Human-to-Robot Embodied Learning from Multi-Source Motion Data for Mobile Dexterous Manipulation** [[paper](https://arxiv.org/abs/2508.20085)]
- [2025] **Correspondence-Free, Function-Based Sim-to-Real Learning for Deformable Surface Control** [[paper](https://arxiv.org/abs/2509.00060)]
- [2025] **Impedance Primitive-augmented Hierarchical Reinforcement Learning for Sequential Tasks** [[paper](https://arxiv.org/abs/2508.19607)]

[⬆ Back to top](#paper-list)

#### Application

##### 2026

- [2026] **Ep. 1059: Google's World Models: The Shift from Chatbots to Reality** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.19362286)]
- [2026] **MolmoB0T: Large-Scale Simulation Enables Zero-Shot Manipulation** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.16861)]

[⬆ Back to top](#paper-list)

#### Development

##### 2026

- [2026] **RflySimVision: A distributed hardware-in-the-loop sim-to-real simulator for vision-based unmanned swarm system** *Robotics and Autonomous Systems* [[paper](https://doi.org/10.1016/j.robot.2026.105417)]

[⬆ Back to top](#paper-list)

#### Systems & Technology

##### 2026

- [2026] **Open-DiffLoco: Open-Source Differentiable Learning for Deployable Blind Quadruped Locomotion** [[paper](https://arxiv.org/abs/2608.02069)]
- [2026] **Is Forward Prediction Enough? Physical State Grounding for JEPA World Models** [[paper](https://arxiv.org/abs/2608.06799)]
- [2026] **GWM-VLA: Geometry-Aware Latent World Modeling for Vision-Language-Action Learning** [[paper](https://arxiv.org/abs/2608.07619)]
- [2026] **PBD-AG: Persistent Baseline-Delta Active Graphs with Uncertainty-Aware Inspection for Long-Horizon Service Robots** [[paper](https://arxiv.org/abs/2608.10449)]
- [2026] **JoyAI-RA 0.5: Scaling Robot Manipulation Learning via Dual Action Alignment** [[paper](https://arxiv.org/abs/2608.05674)]
- [2026] **Surgical WAM: A World-Action Model for Data-Efficient Surgical Robot Learning** [[paper](https://arxiv.org/abs/2608.11204)]
- [2026] **XEWorld: Can Action-Conditioned World Models Generalize to Unseen Robot Embodiments?** [[paper](https://arxiv.org/abs/2608.05799)]
- [2026] **Wearing A Coat: Dual-Arm Robot-Assisted Dressing with Differentiable Clothing Simulation** [[paper](https://arxiv.org/abs/2607.10999)]
- [2026] **ViTacWorld: Scaling Visuo-Tactile World Models for Contact-Rich Robot Manipulation** [[paper](https://arxiv.org/abs/2607.22530)]
- [2026] **BWM: A Low-Cost High-Fidelity World Simulator for Robot Learning** [[paper](https://arxiv.org/abs/2607.29302)]
- [2026] **Path Planning in Physically Viable World Models** [[paper](https://arxiv.org/abs/2607.00673)]
- [2026] **DriftWorld: Fast World Modeling through Drifting** [[paper](https://arxiv.org/abs/2607.15065)]
- [2026] **PhysMani: Physics-principled 3D World Model for Dynamic Object Manipulation** [[paper](https://arxiv.org/abs/2607.01938)]
- [2026] **GigaWorld-1: A Roadmap to Build World Models for Robot Policy Evaluation** [[paper](https://arxiv.org/abs/2607.02642)]
- [2026] **Masked Visual Actions for Unified World Modeling** [[paper](https://arxiv.org/abs/2607.19343)]
- [2026] **Action-Conditioned World Model for Goal Plane Probe Guidance in Robotic Ultrasound** [[paper](https://arxiv.org/abs/2607.21918)]
- [2026] **NeuralActuator: Neural Actuation Modeling for Robot Dynamics and External Force Perception** [[paper](https://arxiv.org/abs/2607.11734)]
- [2026] **WorldDiT: A Unified Diffusion Architecture for World and Action Modeling** [[paper](https://arxiv.org/abs/2607.23909)]
- [2026] **Mask2Real-WM: Segmentation Masks as a Sim-to-Real Bridge for Controllable Dexterous World Models** [[paper](https://arxiv.org/abs/2607.04546)]
- [2026] **Learning Transferable Dynamics Priors from Action to World Modeling** [[paper](https://arxiv.org/abs/2606.29501)]
- [2026] **RigPI: Dynamic Parameter Identification of Rigid Body via VLM-Seeded Differentiable Simulation** [[paper](https://arxiv.org/abs/2606.25212)]
- [2026] **NavWAM: A Navigation World Action Model for Goal-Conditioned Visual Navigation** [[paper](https://arxiv.org/abs/2606.13494)]
- [2026] **Targeting World Models to Compromise Robot Learning Pipelines** [[paper](https://arxiv.org/abs/2606.09499)]
- [2026] **Robots Need More than VLA and World Models** [[paper](https://arxiv.org/abs/2606.06556)]
- [2026] **Continual Robot Policy Learning via Variational Neural Dynamics** [[paper](https://arxiv.org/abs/2606.27353)]
- [2026] **Foresight: Failure Detection for Long-Horizon Robotic Manipulation with Action-Conditioned World Model Latents** [[paper](https://arxiv.org/abs/2606.23085)]
- [2026] **JoyAI-Sim: A Simulation-Enabled Interconversion Toolchain for the Embodied Data Pyramid** [[paper](https://arxiv.org/abs/2606.16776)]
- [2026] **Wh0: Generative World Models as Scalable Sources of Egocentric Human Hand Manipulation Data** [[paper](https://arxiv.org/abs/2606.22136)]
- [2026] **$ω$-EVA: Envision, Verify, and Act with Latent Interactive World Models** [[paper](https://arxiv.org/abs/2606.09457)]
- [2026] **Asymmetric physics enables efficient learning in quadrupedal robot swarms** [[paper](https://arxiv.org/abs/2606.23153)]
- [2026] **WEAVER, Better, Faster, Longer: An Effective World Model for Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.13672)]
- [2026] **In-Context World Modeling for Robotic Control** [[paper](https://arxiv.org/abs/2606.26025)]
- [2026] **GROVE: Grounded Pedestrian Simulation via Natural Language for Interactive Social Robot Navigation** [[paper](https://arxiv.org/abs/2606.25504)]
- [2026] **Learning Action-Conditional and Object-Centric Gaussian Splatting World Models for Rigid Objects** [[paper](https://arxiv.org/abs/2606.01950)]
- [2026] **Generalization of World Models under Environmental Variability for Vision-based Quadrotor Navigation** [[paper](https://arxiv.org/abs/2606.05015)]
- [2026] **OASIS: From Simulation Data Collection to Real-World Humanoid Loco-Manipulation** [[paper](https://arxiv.org/abs/2606.08548)]
- [2026] **World-Language-Action Model for Unified World Modeling, Language Reasoning, and Action Synthesis** [[paper](https://arxiv.org/abs/2606.05979)]
- [2026] **RoboGaze: Evaluating Robot World Models via Structured Vision-Language Analysis** [[paper](https://arxiv.org/abs/2606.28385)]
- [2026] **OrbiSim: World Models as Differentiable Physics Engines for Embodied Intelligence** [[paper](https://arxiv.org/abs/2605.16395)]
- [2026] **$τ_0$-WM: A Unified Video-Action World Model for Robotic Manipulation** [[paper](https://arxiv.org/abs/2606.01027)]
- [2026] **World Models for Robotic Manipulation: A Survey** [[paper](https://arxiv.org/abs/2606.00113)]
- [2026] **GEM-4D: Geometry-Enhanced Video World Models for Robot Manipulation** [[paper](https://arxiv.org/abs/2605.22882)]
- [2026] **STR Robot: Design of an Autonomous Mobile Robot from Simulation to Reality** [[paper](https://arxiv.org/abs/2605.28110)]
- [2026] **Silent Failures in Physical AI: A Literature Review of Runtime Action Authorization for Autonomous Systems** [[paper](https://arxiv.org/abs/2606.00090)]
- [2026] **WorldArena 2.0: Extending Embodied World Model Benchmarking on Modality, Functionality and Platform** [[paper](https://arxiv.org/abs/2605.17912)]
- [2026] **SKIP: Sparse Keyframe Interpolation Paradigm for Efficient Embodied World Models** [[paper](https://arxiv.org/abs/2606.00664)]
- [2026] **Trajectory-based actuator identification via differentiable simulation** [[paper](https://arxiv.org/abs/2604.10351)]
- [2026] **World Model for Robot Learning: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2605.00080)]
- [2026] **RoboWM-Bench: A Benchmark for Evaluating World Models in Robotic Manipulation** [[paper](https://arxiv.org/abs/2604.19092)]
- [2026] **ComSim: Building Scalable Real-World Robot Data Generation via Compositional Simulation** [[paper](https://arxiv.org/abs/2604.11386)]
- [2026] **dWorldEval: Scalable Robotic Policy Evaluation via Discrete Diffusion World Model** [[paper](https://arxiv.org/abs/2604.22152)]
- [2026] **Open-H-Embodiment: A Large-Scale Dataset for Enabling Foundation Models in Medical Robotics** [[paper](https://arxiv.org/abs/2604.21017)]
- [2026] **Toward Hardware-Agnostic Quadrupedal World Models via Morphology Conditioning** [[paper](https://arxiv.org/abs/2604.08780)]
- [2026] **Learning Task-Invariant Properties via Dreamer: Enabling Efficient Policy Transfer for Quadruped Robots** [[paper](https://arxiv.org/abs/2604.02911)]
- [2026] **Mask World Model: Predicting What Matters for Robust Robot Policy Learning** [[paper](https://arxiv.org/abs/2604.19683)]
- [2026] **Few-Shot Neural Differentiable Simulator: Real-to-Sim Rigid-Contact Modeling** [[paper](https://arxiv.org/abs/2603.06218)]
- [2026] **Interactive World Simulator for Robot Policy Training and Evaluation** [[paper](https://arxiv.org/abs/2603.08546)]
- [2026] **IndoorR2X: Indoor Robot-to-Everything Coordination with LLM-Driven Planning** [[paper](https://arxiv.org/abs/2603.20182)]
- [2026] **Simulation Distillation: Pretraining World Models in Simulation for Rapid Real-World Adaptation** [[paper](https://arxiv.org/abs/2603.15759)]
- [2026] **WestWorld: A Knowledge-Encoded Scalable Trajectory World Model for Diverse Robotic Systems** [[paper](https://arxiv.org/abs/2603.14392)]
- [2026] **HALO:Closing Sim-to-Real Gap for Heavy-loaded Humanoid Agile Motion Skills via Differentiable Simulation** [[paper](https://arxiv.org/abs/2603.15084)]
- [2026] **PlayWorld: Learning Robot World Models from Autonomous Play** [[paper](https://arxiv.org/abs/2603.09030)]
- [2026] **Self-adapting Robotic Agents through Online Continual Reinforcement Learning with World Model Feedback** [[paper](https://arxiv.org/abs/2603.04029)]
- [2026] **Towards Practical World Model-based Reinforcement Learning for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2603.20607)]
- [2026] **RAFL: Generalizable Sim-to-Real of Soft Robots with Residual Acceleration Field Learning** [[paper](https://arxiv.org/abs/2603.22039)]
- [2026] **ProgressVLA: Progress-Guided Diffusion Policy for Vision-Language Robotic Manipulation** [[paper](https://arxiv.org/abs/2603.27670)]
- [2026] **Chain of World: World Model Thinking in Latent Motion** [[paper](https://arxiv.org/abs/2603.03195)]
- [2026] **World-Gymnast: Training Robots with Reinforcement Learning in a World Model** [[paper](https://arxiv.org/abs/2602.02454)]
- [2026] **Smoothly Differentiable and Efficiently Vectorizable Contact Manifold Generation** [[paper](https://arxiv.org/abs/2602.20304)]
- [2026] **DreamDojo: A Generalist Robot World Model from Large-Scale Human Videos** [[paper](https://arxiv.org/abs/2602.06949)]
- [2026] **AdaWorldPolicy: World-Model-Driven Diffusion Policy with Online Adaptive Learning for Robotic Manipulation** [[paper](https://arxiv.org/abs/2602.20057)]
- [2026] **Learning to unfold cloth: Scaling up world models to deformable object manipulation** [[paper](https://arxiv.org/abs/2602.16675)]
- [2026] **World-VLA-Loop: Closed-Loop Learning of Video World Model and VLA Policy** [[paper](https://arxiv.org/abs/2602.06508)]
- [2026] **LDA-1B: Scaling Latent Dynamics Action Model via Universal Embodied Data Ingestion** [[paper](https://arxiv.org/abs/2602.12215)]
- [2026] **SoMA: A Real-to-Sim Neural Simulator for Robotic Soft-body Manipulation** [[paper](https://arxiv.org/abs/2602.02402)]
- [2026] **PointWorld: Scaling 3D World Models for In-The-Wild Robotic Manipulation** [[paper](https://arxiv.org/abs/2601.03782)]
- [2026] **Video Generation Models in Robotics -- Applications, Research Challenges, Future Directions** [[paper](https://arxiv.org/abs/2601.07823)]
- [2026] **Causal World Modeling for Robot Control** [[paper](https://arxiv.org/abs/2601.21998)]
- [2026] **InternVLA-A1: Unifying Understanding, Generation and Action for Robotic Manipulation** [[paper](https://arxiv.org/abs/2601.02456)]
- [2026] **Towards Bridging the Gap between Large-Scale Pretraining and Efficient Finetuning for Humanoid Control** [[paper](https://arxiv.org/abs/2601.21363)]

##### 2025

- [2025] **AnchorDream: Repurposing Video Diffusion for Embodiment-Aware Robot Data Synthesis** [[paper](https://arxiv.org/abs/2512.11797)]
- [2025] **MIND-V: Hierarchical World Model for Long-Horizon Robotic Manipulation with RL-based Physical Alignment** [[paper](https://arxiv.org/abs/2512.06628)]
- [2025] **Unifying Deep Predicate Invention with Pre-trained Foundation Models** [[paper](https://arxiv.org/abs/2512.17992)]
- [2025] **STORM: Search-Guided Generative World Models for Robotic Manipulation** [[paper](https://arxiv.org/abs/2512.18477)]
- [2025] **SIMPACT: Simulation-Enabled Action Planning using Vision-Language Models** [[paper](https://arxiv.org/abs/2512.05955)]
- [2025] **RynnVLA-002: A Unified Vision-Language-Action and World Model** [[paper](https://arxiv.org/abs/2511.17502)]
- [2025] **Reinforcing Action Policies by Prophesying** [[paper](https://arxiv.org/abs/2511.20633)]
- [2025] **Stein-based Optimization of Sampling Distributions in Model Predictive Path Integral Control** [[paper](https://arxiv.org/abs/2511.02015)]
- [2025] **WMPO: World Model-based Policy Optimization for Vision-Language-Action Models** [[paper](https://arxiv.org/abs/2511.09515)]
- [2025] **Scaling Cross-Embodiment World Models for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2511.01177)]
- [2025] **From Discrete Plans to Real-World Execution: A World-Model-Driven Framework for Execution-Aware Multi-Agent Path Finding** [[paper](https://arxiv.org/abs/2511.21886)]
- [2025] **ReGen: Generative Robot Simulation via Inverse Design** [[paper](https://arxiv.org/abs/2511.04769)]
- [2025] **URDF-Anything: Constructing Articulated Objects with 3D Multimodal Language Model** [[paper](https://arxiv.org/abs/2511.00940)]
- [2025] **Quadrotor Navigation using Reinforcement Learning with Privileged Information** [[paper](https://arxiv.org/abs/2509.08177)]
- [2025] **DynaFlow: Dynamics-embedded Flow Matching for Physically Consistent Motion Generation from State-only Demonstrations** [[paper](https://arxiv.org/abs/2509.19804)]
- [2025] **Learning on the Fly: Rapid Policy Adaptation via Differentiable Simulation** [[paper](https://arxiv.org/abs/2508.21065)]

[⬆ Back to top](#paper-list)

#### Evaluation & Benchmarks

##### 2026

- [2026] **Sim-to-real transfer by hybrid Gaussian Splatting and geometric reconstruction for autonomous driving** *Engineering Applications of Artificial Intelligence* [[paper](https://doi.org/10.1016/j.engappai.2026.114372)]

[⬆ Back to top](#paper-list)

### Surveys & Taxonomies

#### Theory

##### 2026

- [2026] **Path Planning for Multiple Mobile Robots: A Systematic Review Using Parameter-Mapped Benchmarking** *Machines* [[paper](https://doi.org/10.3390/machines14080870)]
- [2026] **Reinforcement Learning for Diffusion Policies in Robotics: A Survey and State-Based Locomotion Reproduction** *Robotics* [[paper](https://doi.org/10.3390/robotics15080147)]
- [2026] **Mobile Robot Localization and SLAM: A Critical Review of Sensors, Multi-Sensor Fusion, and Neural Representations** *Robotics* [[paper](https://doi.org/10.3390/robotics15080142)]
- [2026] **Recent advances in AI-based mobile robots for human companionship: survey** *Artificial Intelligence Review* [[paper](https://doi.org/10.1007/s10462-026-11603-9)]
- [2026] **Sensing the Action: Rethinking Sensor Modalities and Multi-Modal Fusion in Vision–Language–Action Models for Robotic Manipulation** *Sensors* [[paper](https://doi.org/10.3390/s26113541)]
- [2026] **Multi-agent task and motion planning trends analysis: a survey** *Artificial Intelligence Review* [[paper](https://doi.org/10.1007/s10462-026-11588-5)]
- [2026] **World Models: A Comprehensive Survey of Architectures, Methodologies, Reasoning Paradigms, and Applications** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2606.00133)]
- [2026] **World Models and World Action Models (WAM): From Foundation Simulators to Embodied Action** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20046240)]
- [2026] **Editorial** *Journal of Engineering Design and Technology* [[paper](https://doi.org/10.1108/jedt-05-2026-754)]
- [2026] **How large-scale foundation models benefit precision livestock farming: A survey** *Artificial Intelligence in Agriculture* [[paper](https://doi.org/10.1016/j.aiia.2026.04.013)]
- [2026] **Replication materials for the paper "Engineering LLM-Based Multi-Agent Systems: A Taxonomy of Emerging Frameworks"** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.19919085)]
- [2026] **A Survey-Driven Framework for Autonomous Mobile Robot Navigation Systems: The Perception–Cognition–Operation (PCO) Approach** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202603.0528.v1)]
- [2026] **Speculative Decoding for Multimodal Models: A Survey** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202603.2344.v1)]
- [2026] **Surface Offsetting: A Survey From Geometric Construction to Neural Implicit Representations** *IEEE Transactions on Visualization and Computer Graphics* [[paper](https://doi.org/10.1109/tvcg.2026.3676903)]

[⬆ Back to top](#paper-list)

#### Mechanism

##### 2026

- [2026] **Memory in Vision-Language Models: Taxonomy, Mechanisms, and Applications** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202607.1539.v1)]
- [2026] **Cooperative Perception for Multi-Robot Systems in Natural Outdoor Applications – A Survey** *Journal of Intelligent & Robotic Systems* [[paper](https://doi.org/10.1007/s10846-026-02404-x)]
- [2026] **Evolutionary Algorithms and Engineering Applications: A Comprehensive Survey of Classical Methods and Emerging Trends** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202606.0126.v1)]
- [2026] **A Survey of Agent Skills: Toward Procedural Infrastructure for LLM Agents** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202605.1276.v1)]
- [2026] **Computer Vision for Collaborative Robots in Industry 5.0: A Survey of Techniques, Gaps, and Future Directions** [[paper](https://doi.org/10.3390/engproc2026124099)]
- [2026] **Talking Head Generation Through Generative Models and Cross-Modal Synthesis Techniques** *Journal of Imaging* [[paper](https://doi.org/10.3390/jimaging12030119)]

[⬆ Back to top](#paper-list)

#### Method

##### 2026

- [2026] **Developing Freshwater Aquatic Invasive Species Watch Lists for British Columbia, Canada and Identifying Possible Early Detection Methods** *ARPHA Conference Abstracts* [[paper](https://doi.org/10.3897/aca.9.e202246)]
- [2026] **A Survey of Sim-to-Real Transfer Methods in Robot Learning.** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.21101584)]
- [2026] **Evolutionary algorithms as information fusion architectures: A survey** *Information Fusion* [[paper](https://doi.org/10.1016/j.inffus.2026.104578)]
- [2026] **Lifelong Representations: A Survey on Continual Self-Supervised Learning for Vision Models** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.09785)]
- [2026] **Rethinking Multi-Label Image Classification With Deep Learning: Taxonomy, Challenge, and Outlook** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.00839)]
- [2026] **Hand-Object Interaction in the Age of Large Foundation Models:Reconstruction, Generation, and Embodied Transfer** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2607.28394)]
- [2026] **Predicting the World via Video Representation: A Comprehensive Survey on Video World Models** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202605.0435.v1)]
- [2026] **Advances in Feed‐Forward 3D Reconstruction and View Synthesis: A Survey** *Computer Graphics Forum* [[paper](https://arxiv.org/abs/2507.14501)]
- [2026] **Planning and Evaluation Methods in LLM-Based Autonomous Workflow Systems: A Comprehensive Review** *Research Square* [[paper](https://doi.org/10.21203/rs.3.rs-9460995/v1)]
- [2026] **Agentic AI Systems for Pattern Analysis and Machine Intelligence: A Layered Survey of Architectures, Evaluation, and Safety** *Zenodo (CERN European Organization for Nuclear Research)* [[paper](https://doi.org/10.5281/zenodo.20247605)]
- [2026] **Memristor Technologies for Dynamic Vision Sensors: A Critical Assessment and Research Roadmap** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2605.13699)]
- [2026] **Multi-Modal Radiance Fields in Robotics: A Survey** [[paper](https://doi.org/10.1109/iccc68994.2026.11511655)]
- [2026] **A Survey of Embodied World Models** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202604.0928.v1)]
- [2026] **A survey of deep learning techniques for image-based disease detection in dicot plants** *Information Processing in Agriculture* [[paper](https://doi.org/10.1016/j.inpa.2026.03.014)]
- [2026] **Collaboration in Multi-Robot Systems: Taxonomy and Survey over Frameworks for Collaboration** *arXiv (Cornell University)* [[paper](https://arxiv.org/abs/2603.23898)]
- [2026] **Robot localization: a comprehensive survey from classical methods to intelligent autonomy** *International Journal of Intelligent Robotics and Applications* [[paper](https://doi.org/10.1007/s41315-026-00528-9)]
- [2026] **Robotic and AI Enabled Waste Segregation A Systematic Review of Methods Benchmarks and Challenges** *Research Square* [[paper](https://doi.org/10.21203/rs.3.rs-8474173/v1)]
- [2026] **A Comprehensive Review of Generative Physical Artificial Intelligence** *IEEE Internet of Things Journal* [[paper](https://doi.org/10.1109/jiot.2026.3671268)]
- [2026] **A Survey of Continual Learning for Robotics in the Foundation Model Era** [[paper](https://doi.org/10.36227/techrxiv.176972367.76460794/v3)]

[⬆ Back to top](#paper-list)

#### Application

##### 2026

- [2026] **Orchestrating LLMs with Specialized Models: A Survey on Heterogeneous Multi-Model Agents** *Preprints.org* [[paper](https://doi.org/10.20944/preprints202607.1041.v1)]

[⬆ Back to top](#paper-list)

#### Evaluation & Benchmarks

##### 2026

- [2026] **Many-objective hyper-heuristics: A state-of-the-art survey** *Computer Science Review* [[paper](https://doi.org/10.1016/j.cosrev.2026.100971)]

[⬆ Back to top](#paper-list)

#### Reviews & Surveys

##### 2026

- [2026] **Weights or Skills? A Survey of Robot-Learning Techniques: from Action-Predicting Weights to Robots that Write their Own Skills** [[paper](https://arxiv.org/abs/2608.01851)]
- [2026] **From Operational Design Domain to Action: A Systematic Behavioral Taxonomy for Autonomous Driving** [[paper](https://arxiv.org/abs/2608.08941)]
- [2026] **A Comprehensive Survey and Systematic Real-World Evaluation of Embodied Vision-and-Language Navigation** [[paper](https://arxiv.org/abs/2607.09792)]
- [2026] **Coverage Path Planning: Classical Foundations, Recent Advances, and Future Directions** [[paper](https://arxiv.org/abs/2607.10649)]
- [2026] **The Three Dimensions of ROS 2 Middleware** [[paper](https://arxiv.org/abs/2607.01304)]
- [2026] **More Structure, Not More Capacity: Object-Centric Representations for Visuomotor Imitation Learning** [[paper](https://arxiv.org/abs/2607.09825)]
- [2026] **Beyond correlation: a survey on causal inference for dynamics-aware perception and introspective decision-making in robotics** *Nonlinear Dynamics* [[paper](https://doi.org/10.1007/s11071-026-12695-2)]
- [2026] **3D point cloud processing and analysis: a survey** *Multimedia Tools and Applications* [[paper](https://doi.org/10.1007/s11042-026-21797-3)]
- [2026] **SoK: Security and Privacy of Foundation-Model-Powered Robots** [[paper](https://arxiv.org/abs/2606.16788)]
- [2026] **3D Scene Graphs: Open Challenges and Future Directions** [[paper](https://arxiv.org/abs/2606.19383)]
- [2026] **NVIDIA Isaac Sim: Enabling Scalable, GPU-Accelerated Simulation for Robotics** [[paper](https://arxiv.org/abs/2606.03551)]
- [2026] **When Stopping Fails: Rethinking Minimal Risk Conditions through Human-Interactive Autonomous Driving for Safe Transportation Systems** [[paper](https://arxiv.org/abs/2606.29115)]
- [2026] **Intelligent Automation for Embodied Benchmark Construction: Pipelines, Embodiments, Simulators, and Trends** [[paper](https://arxiv.org/abs/2606.12207)]
- [2026] **Vision-Language Models for Deployable Social Robot Navigation: Bridging Semantic Reasoning and Low-Level Control** [[paper](https://arxiv.org/abs/2606.28760)]
- [2026] **Multi-Agent Embodied Autonomous Driving: From V2X Information Exchange to Shared World Models** [[paper](https://arxiv.org/abs/2606.13840)]
- [2026] **From Human Videos to Robot Manipulation: A Survey on Scalable Vision-Language-Action Learning with Human-Centric Data** [[paper](https://arxiv.org/abs/2606.00054)]
- [2026] **Towards Robotic Dexterous Hand Intelligence: A Survey** [[paper](https://arxiv.org/abs/2605.13925)]
- [2026] **Prior Availability in Industrial Visual Sim-to-Real: A Review of CAD-Guided and CAD-Unavailable Regimes** [[paper](https://arxiv.org/abs/2605.30581)]
- [2026] **Artificial Intelligence for Modeling and Simulation of Mixed Automated and Human Traffic** [[paper](https://arxiv.org/abs/2604.12857)]
- [2026] **Robot Learning from Human Videos: A Survey** [[paper](https://arxiv.org/abs/2604.27621)]
- [2026] **On-Orbit Space AI: Federated, Multi-Agent, and Collaborative Algorithms for Satellite Constellations** [[paper](https://arxiv.org/abs/2604.16518)]
- [2026] **Vision-Language Navigation for Aerial Robots: Towards the Era of Large Language Models** [[paper](https://arxiv.org/abs/2604.07705)]
- [2026] **From Video to Control: A Survey of Learning Manipulation Interfaces from Temporal Visual Data** [[paper](https://arxiv.org/abs/2604.04974)]
- [2026] **A Systematic Review and Taxonomy of Reinforcement Learning-Model Predictive Control Integration for Linear Systems** [[paper](https://arxiv.org/abs/2604.21030)]
- [2026] **A Survey on Sensor-based Planning and Control for Unmanned Underwater Vehicles** [[paper](https://arxiv.org/abs/2604.05003)]
- [2026] **Singularity Avoidance in Inverse Kinematics: A Unified Treatment of Classical and Learning-based Methods** [[paper](https://arxiv.org/abs/2604.13405)]
- [2026] **Towards Next-Generation Healthcare: A Survey of Medical Embodied AI for Perception, Decision-Making, and Action** [[paper](https://arxiv.org/abs/2606.15647)]
- [2026] **Human Cognition in Machines: A Unified Perspective of World Models** [[paper](https://arxiv.org/abs/2604.16592)]
- [2026] **Safety, Security, and Cognitive Risks in World Models** [[paper](https://arxiv.org/abs/2604.01346)]
- [2026] **Safety in Embodied AI: A Survey of Risks, Attacks, and Defenses** [[paper](https://arxiv.org/abs/2605.02900)]
- [2026] **Underwater Embodied Intelligence for Autonomous Robots: A Constraint-Coupled Perspective on Planning, Control, and Deployment** [[paper](https://arxiv.org/abs/2603.07393)]
- [2026] **Uni-Skill: Building Self-Evolving Skill Repository for Generalizable Robotic Manipulation** [[paper](https://arxiv.org/abs/2603.02623)]
- [2026] **Deep Learning-Based Point Cloud Registration: A Comprehensive Survey and Taxonomy** *International Journal of Computer Vision* [[paper](https://doi.org/10.1007/s11263-025-02723-w)]
- [2026] **Advances in Global Solvers for 3D Vision** [[paper](https://arxiv.org/abs/2602.14662)]
- [2026] **From Perception to Action: Spatial AI Agents and World Models** [[paper](https://arxiv.org/abs/2602.01644)]
- [2026] **Cybersecurity of Teleoperated Quadruped Robots: A Systematic Survey of Vulnerabilities, Threats, and Open Defense Gaps** [[paper](https://arxiv.org/abs/2602.23404)]
- [2026] **Towards Next-Generation SLAM: A Survey on 3DGS-SLAM Focusing on Performance, Robustness, and Future Directions** [[paper](https://arxiv.org/abs/2602.04251)]
- [2026] **A Comprehensive Survey on Deep Learning-Based LiDAR Super-Resolution for Autonomous Driving** [[paper](https://arxiv.org/abs/2602.15904)]
- [2026] **A Decade of Human-Robot Interaction Through Immersive Lenses: Reviewing Extended Reality as a Research Instrument in Social Robotics** [[paper](https://arxiv.org/abs/2602.15840)]
- [2026] **A Review of Online Diffusion Policy RL Algorithms for Scalable Robotic Control** [[paper](https://arxiv.org/abs/2601.06133)]
- [2026] **Advancing Improvisation in Human-Robot Construction Collaboration: Taxonomy and Research Roadmap** [[paper](https://arxiv.org/abs/2601.17219)]
- [2026] **Benchmarking Autonomy in Scientific Experiments: A Hierarchical Taxonomy for Autonomous Large-Scale Facilities** [[paper](https://arxiv.org/abs/2601.06978)]
- [2026] **Advanced techniques and applications of LiDAR Place Recognition in Agricultural Environments: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2601.22198)]

##### 2025

- [2025] **Embodied Co-Design for Rapidly Evolving Agents: Taxonomy, Frontiers, and Challenges** [[paper](https://arxiv.org/abs/2512.04770)]
- [2025] **A Survey of Real-Time Support, Analysis, and Advancements in ROS 2** [[paper](https://arxiv.org/abs/2601.10722)]
- [2025] **Toward Seamless Physical Human-Humanoid Interaction: Insights from Control, Intent, and Modeling with a Vision for What Comes Next** [[paper](https://arxiv.org/abs/2512.07765)]
- [2025] **Trust in LLM-controlled Robotics: a Survey of Security Threats, Defenses and Challenges** [[paper](https://arxiv.org/abs/2601.02377)]
- [2025] **Embodied Robot Manipulation in the Era of Foundation Models: Planning and Learning Perspectives** [[paper](https://arxiv.org/abs/2512.22983)]
- [2025] **An Anatomy of Vision-Language-Action Models: From Modules to Milestones and Challenges** [[paper](https://arxiv.org/abs/2512.11362)]
- [2025] **Taxonomy and Modular Tool System for Versatile and Effective Non-Prehensile Manipulations** [[paper](https://arxiv.org/abs/2512.11080)]
- [2025] **Incremental Validation of Automated Driving Functions using Generic Volumes in Micro- Operational Design Domains** [[paper](https://arxiv.org/abs/2512.11351)]
- [2025] **Movement Primitives in Robotics: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2601.02379)]
- [2025] **Towards a Unified Understanding of Robot Manipulation: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2510.10903)]
- [2025] **Foundation Models for Trajectory Planning in Autonomous Driving: A Review of Progress and Open Challenges** [[paper](https://arxiv.org/abs/2512.00021)]
- [2025] **Integrating Legal and Logical Specifications in Perception, Prediction, and Planning for Automated Driving: A Survey of Methods** [[paper](https://arxiv.org/abs/2510.25386)]
- [2025] **A Comprehensive Survey on Surgical Digital Twin** [[paper](https://arxiv.org/abs/2512.00019)]
- [2025] **Taxonomy and Trends in Reinforcement Learning for Robotics and Control Systems: A Structured Review** [[paper](https://arxiv.org/abs/2510.21758)]
- [2025] **A short methodological review on social robot navigation benchmarking** [[paper](https://arxiv.org/abs/2510.22448)]
- [2025] **Vision-Language-Action Models for Robotics: A Review Towards Real-World Applications** [[paper](https://arxiv.org/abs/2510.07077)]
- [2025] **DexCanvas: Bridging Human Demonstrations and Robot Learning for Dexterous Manipulation** [[paper](https://arxiv.org/abs/2510.15786)]
- [2025] **Efficient Vision-Language-Action Models for Embodied Manipulation: A Systematic Survey** [[paper](https://arxiv.org/abs/2510.17111)]
- [2025] **Semantic Visual Simultaneous Localization and Mapping: A Survey on State of the Art, Challenges, and Future Directions** [[paper](https://arxiv.org/abs/2510.00783)]
- [2025] **A Step Toward World Models: A Survey on Robotic Manipulation** [[paper](https://arxiv.org/abs/2511.02097)]
- [2025] **A Literature Review On Stewart-Gough Platform Calibrations A Literature Review On Stewart-Gough Platform Calibrations** [[paper](https://arxiv.org/abs/2510.21854)]
- [2025] **Pure Vision Language Action (VLA) Models: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2509.19012)]
- [2025] **Foundation Models for Autonomous Driving Perception: A Survey Through Core Capabilities** [[paper](https://arxiv.org/abs/2509.08302)]
- [2025] **3D and 4D World Modeling: A Survey** [[paper](https://arxiv.org/abs/2509.07996)]
- [2025] **A Nascent Taxonomy of Machine Learning in Intelligent Robotic Process Automation** [[paper](https://arxiv.org/abs/2509.15730)]
- [2025] **Revisiting Formal Methods for Autonomous Robots: A Structured Survey** [[paper](https://arxiv.org/abs/2509.20488)]
- [2025] **A Comprehensive Review of Reinforcement Learning for Autonomous Driving in the CARLA Simulator** [[paper](https://arxiv.org/abs/2509.08221)]
- [2025] **Taxonomy-aware Dynamic Motion Generation on Hyperbolic Manifolds** [[paper](https://arxiv.org/abs/2509.21281)]
- [2025] **Adaptive Cruise Control in Autonomous Vehicles: Challenges, Gaps, Comprehensive Review, and, Future Directions** [[paper](https://arxiv.org/abs/2510.03300)]
- [2025] **Scenario-based Decision-making Using Game Theory for Interactive Autonomous Driving: A Survey** [[paper](https://arxiv.org/abs/2509.05777)]
- [2025] **HOGraspFlow: Taxonomy-Aware Hand-Object Retargeting for Multi-Modal SE(3) Grasp Generation** [[paper](https://arxiv.org/abs/2509.16871)]
- [2025] **Online Clustering of Seafloor Imagery for Interpretation during Long-Term AUV Operations** [[paper](https://arxiv.org/abs/2509.06678)]
- [2025] **Timing the Message: Language-Based Notifications for Time-Critical Assistive Settings** [[paper](https://arxiv.org/abs/2509.07438)]
- [2025] **Large Foundation Models for Trajectory Prediction in Autonomous Driving: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2509.10570)]
- [2025] **From Static to Dynamic: a Survey of Topology-Aware Perception in Autonomous Driving** [[paper](https://arxiv.org/abs/2509.23641)]
- [2025] **To New Beginnings: A Survey of Unified Perception in Autonomous Vehicle Software** [[paper](https://arxiv.org/abs/2508.20892)]
- [2025] **M3DMap: Object-aware Multimodal 3D Mapping for Dynamic Environments** [[paper](https://arxiv.org/abs/2508.17044)]
- [2025] **Sensing, Social, and Motion Intelligence in Embodied Navigation: A Comprehensive Survey** [[paper](https://arxiv.org/abs/2508.15354)]

[⬆ Back to top](#paper-list)

## 📖 Citation

If you use this corpus, please cite:

```bibtex
@misc{robotics-research,
  author = {Weiß, Tobias},
  title = {Robotics Research Corpus: Data-Driven Agentic Literature Review},
  year = {2026},
  publisher = {GitHub},
  url = {https://github.com/tobias-weiss-ai-xr/robotics-research}
}
```

## 📄 License

MIT — see [LICENSE](LICENSE).
