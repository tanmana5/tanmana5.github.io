---
title: "New Worlds: Exploring with World Models"
date: 2026-06-02
tags: [llm-agents, planning, world-models, robotics, physical-ai, generative-ai]
---

Think about how you catch a falling cup. You don’t run a billion-parameter calculation on fluid dynamics. Your brain has a built-in "physics engine" trained on a lifetime of drops, spills, and gravity. You anticipate what happens next, and you act (admittedly gravity and other pesky physical forces can be quite annoying sometimes, especially when there's a spillage to clean up :/).

This "brain" is a system that can be represented by a **World Model**.

Instead of treating AI like a text-in, text-out calculator, world models try to give machines an internal understanding of physical reality. But not all world models are built the same. The industry has fractured into entirely different architectural philosophies.

The heavy hitters shaping the frontier of physical AI right now: DeepMind’s Genie 3, NVIDIA’s Cosmos 3, Meta’s V-JEPA 2, and the classic RL pioneer, DreamerV3.

## The Lineup: Different Blueprints for Reality

To understand how these architectures differ, we have to look at what they prioritize: pixel perfection, physical reasoning, or abstract understanding.


### Genie 3: The Interactive Simulator

Recently listened to an exciting podcast episode with DeepMind engineers: [episode](https://twimlai.com/podcast/twimlai/genie-3-a-new-frontier-for-world-models). They provided a detailed picture on the evolution of the Genie project and highlight breakthroughs like Genie3's visual memory and ability to handle “promptable world events.” In particular, I think it would be super interesting to see how to leverage it as a dynamic training environment for embodied AI agents in practice. Genie 3 serves up 720p environments at 24 frames/second, treats video frames and interactive actions as *continuous token sequences*. Recently, DeepMind linked it with Google Street View. While amazing for simulation, it still suffers from typical video generation quirks if pushed past its 60-second exploration limit.

### Cosmos 3: The "Omnimodel" for Physical AI

Physical AI news has been abuzz with the release of the Cosmos 3 model by NVIDIA. It is posited as a foundational model for robotics and autonomous vehicles across the board. Cosmos 3 is a massive, open-source *Mixture-of-Transformers (MoT)* architecture offered in 16B (Nano) and 64B (Super) parameter flavors. It splits the heavy lifting into two distinct "towers":

- A *Reasoner Tower* (a VLM) that observes and understands object interactions and geometry.
- A *Generator Tower* that handles future observations and generates action trajectories.

Its USP is high physics fidelity. It tokenizes video, text, images, and ambient sound alongside action states, yielding synthetic data that strictly respects physical laws (liquids sloshing, rigid collisions, lighting shifts), although it requires large compute infrastructure to leverage at scale

### Meta V-JEPA 2: The Non-Generative Intellectual

Yann LeCun has long argued that generating pixels is a colossal waste of AI brainpower. Meta's *Video Joint Embedding Predictive Architecture (V-JEPA 2)* is the living proof of that philosophy.
V-JEPA 2 completely throws out pixel reconstruction, and instead masks portions of a video and forces the model to predict the missing pieces strictly in latent space (abstract feature space). It may be possible to freeze the model and add a tiny, lightweight layer on top to handle zero-shot robot control (like grasping or pick-and-place) in brand-new environments.
The caveat being, it won't give you a beautiful, human-watchable video simulation. It is essentially a brain without a display monitor.


### DreamerV3: The Reinforcement Learning Classic

While the others are massive foundational models trained on millions of hours of video or robotics data, DreamerV3 learns purely from trial and error. Its the algorithm that famously mastered Minecraft from scratch without any human demonstrations.
The architecture uses a *Recurrent State-Space Model (RSSM)* with discrete categorical representations. It predicts future states, rewards, and continuations inside its own internal "dream" buffer. DreamerV3 uses mathematical tricks like *symlog normalization* to squash highly varying rewards, allowing the exact same model to master a text game, a 2D Atari game, or a complex 3D environment without retuning.
On the downside, it is fundamentally an RL agent's internal engine rather than a multi-purpose visual foundation model like Cosmos or Genie.

## The Philosophical Divide: Pixels vs. Features
Genie 3 and Cosmos 3 represent the *Generative* Camp. They believe that if an AI can generate a physically perfect video of a car crash or a robotic arm dropping a ball, it must inherently understand physics.
V-JEPA 2 represents the *Analytical Camp*. They argue that a robot doesn't need to know how a puddle reflects a neon sign to step over it. By predicting abstract features rather than pixels, V-JEPA 2 bypasses the immense computational tax of generation, focusing purely on common-sense physics and geometry.


## The Sim-to-Real Chasm is Closing
It is well-known that robotics was bottlenecked by data collection for a long time. You couldn't let an expensive robot arm smash into a wall a million times to learn how to avoid it.
Now, with models like Cosmos 3 generating hyper-accurate physical scenarios and Genie 3 turning real-world mapping imagery into interactive playgrounds (like Waymo simulating autonomous edge cases), the "Sim-to-Real" gap should be closing. We are officially entering an era where AI agents train for many years in highly precise digital dreams before ever touching physical hardware.

## References

**Genie 3 (DeepMind, August 2025)**
- [Genie 3: A new frontier for world models](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/) — DeepMind blog announcement
- [Genie 3: A new frontier for world models](https://twimlai.com/podcast/twimlai/genie-3-a-new-frontier-for-world-models) — TWIML podcast with the DeepMind team

**Cosmos 3 (NVIDIA, 2025)**
- [NVIDIA Launches Cosmos 3, the Open Frontier Foundation Model for Physical AI](https://nvidianews.nvidia.com/news/nvidia-launches-cosmos-3-the-open-frontier-foundation-model-for-physical-ai) — NVIDIA newsroom
- [Cosmos World Foundation Model Platform for Physical AI](https://arxiv.org/abs/2501.03575) — original Cosmos technical paper (arXiv:2501.03575)
- [How Cosmos 3 Helps Physical AI Think Before It Acts](https://blogs.nvidia.com/blog/cosmos-3-physical-ai-open-world-foundation-model/) — NVIDIA technical blog

**V-JEPA 2 (Meta, 2025)**
- [V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Planning](https://arxiv.org/abs/2506.09985) — paper (arXiv:2506.09985)
- [Introducing V-JEPA 2](https://ai.meta.com/research/vjepa/) — Meta AI research page

**DreamerV3 (Hafner et al., 2025)**
- [Mastering diverse control tasks through world models](https://www.nature.com/articles/s41586-025-08744-2) — Nature publication
- [Mastering Diverse Domains through World Models](https://arxiv.org/abs/2301.04104) — original arXiv preprint (arXiv:2301.04104)
- [danijar/dreamerv3](https://github.com/danijar/dreamerv3) — official code release