# Learner Profile

Use this file as default context when generating shallow literature review paper or keyword study documents.

## Known Domains

The learner's main background is:

- Statistics
- Machine learning
- Large language models
- Generative models

## Assumed Strengths

The learner can usually handle:

- Basic probability and statistics language.
- Machine learning task framing.
- Training / validation / test splits.
- Model evaluation metrics in ML contexts.
- Neural network and deep learning basics.
- Generative modeling concepts at a high level.
- LLM prompting, fine-tuning, and evaluation ideas at a high level.

## Do Not Over-Explain By Default

Unless the paper uses these ideas in a specialized way, do not spend much space explaining:

- supervised learning
- classification
- regression
- train/test evaluation
- neural networks
- embeddings
- diffusion models at a high level
- LLMs
- generative models
- likelihood / distribution / sampling
- basic optimization intuition

## Likely Gaps Outside The Main Background

For papers outside statistics, ML, LLMs, or generative models, do not assume the learner knows field-specific prerequisites.

Examples:

- Networking: packet, flow, pcap, L3/L4/L7, TCP/UDP, ICMP, BGP, AS, prefix, subnet, PoP, CDN, IGW, tenant, route hijack, RPKI.
- Systems: kernel, dataplane, control plane, DPDK, P4, eBPF, RPC, consensus, cache coherence.
- Security: threat model, adversary capability, authentication, authorization, cryptographic protocol, side channel.
- Databases: transaction, isolation level, query plan, index, replication, consistency.
- Programming languages: type system, operational semantics, compiler pass, IR, runtime.
- Biology/medicine: assay, cohort, endpoint, biomarker, pathway, expression, clinical trial phase.

## Prompting Rule

When using `keyword-prompt.md`, always include this learner profile or summarize it.

The AI tutor should:

- Treat known domains as compressed background.
- Explicitly surface prerequisite concepts outside those domains.
- Mark prerequisite concepts as `P0` or `P1` when they block paper comprehension.
- Distinguish `paper-native keywords` from `learner-bridge keywords`.
