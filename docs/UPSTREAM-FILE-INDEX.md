# Upstream File Index

> Status: partial, source-backed index. This file records paths and Git blob/tree identifiers from upstream Git trees. A listed file is not a license grant to copy it. No upstream payload text is reproduced here.

## Snapshot convention

- `tree_sha`: Git tree object SHA for the inspected branch snapshot; it is not a commit SHA.
- `blob_sha`: Git blob SHA for the exact path at that snapshot.
- Re-check the upstream branch and SHA before importing or implementing.
- Repository code license and dataset/prompt/model-artifact terms must be reviewed independently.
- Dangerous operational payloads are indexed by path and purpose only; the project does not mirror them as runnable jailbreak content.

## AISafetyLab

- Repository: https://github.com/thu-coai/AISafetyLab
- Default branch: `main`
- Inspected tree SHA: `3fd15737dee5c6858466162d6a68e6cb6f996b27`
- Tree response: `truncated=false`
- Repository metadata reports MIT license; this does not automatically license bundled datasets or model artifacts.

| Upstream path | Blob SHA | Indexed role |
|---|---|---|
| `LICENSE` | `bdec0b84d8fb7f480ea5e784534ab3aab5565156` | Code license evidence |
| `README.md` | `c458bb853110955306fc0cfc1d3787a383d3937c` | Framework scope and method inventory |
| `aisafetylab/attack/attackers/advprompter.py` | `ca173b17d682ad346d708fae7c4bcdae47317153` | AdvPrompter attacker implementation |
| `aisafetylab/attack/attackers/autodan.py` | `3a7c0c5e60d705792597bc51e167f9ea4a24bdff` | AutoDAN attacker implementation |
| `aisafetylab/attack/attackers/cipher.py` | `e73479daadfa65d84f84f955c99492cf5fdcfa49` | Cipher-family attacker implementation |
| `aisafetylab/attack/attackers/deep_inception.py` | `9b34c29b05c4e6b1b591e866a34482afc5dfe9e3` | DeepInception implementation |
| `aisafetylab/attack/attackers/dra.py` | `50d5739a2eee8ff752b7bc2d8c9007400469cb7a` | DRA attacker implementation |
| `aisafetylab/attack/attackers/gcg.py` | `186f3ac5337a2806d6ce7e1a24b6e6212ddf9084` | GCG attacker implementation |
| `aisafetylab/attack/attackers/gptfuzzer.py` | `6aea95e0cc12302144d3add5bdd53c753570d13a` | GPTFuzzer implementation |
| `aisafetylab/attack/attackers/ica.py` | `473d10ee845720a6b75828caa644a6678ddf24ec` | ICA implementation |
| `aisafetylab/attack/attackers/jailbroken.py` | `5cbcfcfcb7dbba19832f08743d7ba68889a09719` | JailBroken-family implementation |
| `aisafetylab/attack/attackers/laa.py` | `d64a989ffff2783ddeab66b738ddf4c28170f64f` | LAA implementation |
| `aisafetylab/attack/attackers/multilingual.py` | `7e6fdb45fe925bcbbfa9777a25919caf6ba17b8e` | Multilingual attacker implementation |
| `aisafetylab/attack/attackers/pair.py` | `12e47ba8d476f1bc2acf67d383c1fdbbb45f6d8e` | PAIR implementation |
| `aisafetylab/attack/attackers/rene.py` | `9289b6613648f88fd3139b78b63ea104a9466fcf` | ReNe implementation |
| `aisafetylab/attack/attackers/renellm.py` | `da3ce8c49ff8c533a584879aae011e7d502f4732` | ReNeLLM implementation |
| `aisafetylab/attack/attackers/tap.py` | `78724374756d960fbbd4fdadbb4c655f5f52d627` | TAP implementation |
| `aisafetylab/attack/initialization/seed_template.py` | `556d290b517f60ee29f139e6b4abeb3c3eaf5a63` | Seed/template initialization |
| `aisafetylab/attack/mutation/Translate.py` | `5c969aaa990e44a0e612e7562a0414c302e91e0a` | Translation mutation |
| `aisafetylab/attack/mutation/auto_obfuscation.py` | `8925bc41e2b20bfc63e5aa672237394e3c79ef42` | Obfuscation mutation; path indexed only |
| `aisafetylab/attack/mutation/auto_payload_splitting.py` | `1c8fd11b3668760643787b3abd298e5d92e75a68` | Payload splitting mutation; path indexed only |
| `aisafetylab/attack/mutation/base64.py` | `5b9c6cbc015a3607732e04780d90f4f4e284117c` | Encoding mutation; path indexed only |
| `aisafetylab/attack/mutation/cipher_mutation.py` | `b93a06bc38fc20bffcf9068d7ba9978f41549b29` | Cipher mutation; path indexed only |
| `aisafetylab/attack/mutation/crossover.py` | `ef093fb05ccf877999e06dee017b7ebdf02e8093` | Crossover mutation |
| `aisafetylab/attack/mutation/expand.py` | `27bfbf2eb7bb5000aef5bfd60952fcf9f267ca65` | Expansion mutation |
| `aisafetylab/attack/mutation/generate_similar.py` | `efe9a2599f378cef236cacad8585adabac0a5eaf` | Similar-example generation |
| `aisafetylab/attack/mutation/gradient_sub.py` | `e55fe11f4ae7bdfd805a5d91bdcb919834890013` | Gradient-guided substitution |
| `aisafetylab/attack/mutation/historical_insight.py` | `bce0147dd8c54c3877e05201546ddef0e55d54d9` | Historical feedback mutation |
| `aisafetylab/attack/mutation/introspect_generation.py` | `70d5c637d520e31b450a508ca9c2b74797d5426d` | Introspective generation |
| `aisafetylab/attack/mutation/rephrase.py` | `977b1c7733f3fae634c00833a60e83e39298d8f7` | Rephrase mutation |
| `aisafetylab/attack/mutation/shorten.py` | `abafbc483a612ed7adbb4b4d4f257b38f1bf50a9` | Shorten mutation |
| `aisafetylab/attack/mutation/synonyms.py` | `354c7f8ccdc5312402e5f411a15b436a4171a35d` | Synonym mutation |
| `aisafetylab/attack/dataset/attack_dataset.py` | `b6588c7270234277c8003c1baf0ceb6a7bdb4d27` | Dataset abstraction |
| `aisafetylab/evaluation/scorers/prompted_llm_scorer.py` | `70b4945a4eb05718f35a8a9998705f766fb5c96b` | LLM-based scoring |

Additional data paths were observed under `aisafetylab/attack/attackers/data/icl/` and `aisafetylab/attack/initialization/`. Their contents are not mirrored here; record each dataset file separately with its own terms before reuse.

## HarmBench

- Repository: https://github.com/centerforaisafety/HarmBench
- Default branch: `main`
- Inspected tree SHA: `8e1604d1171fe8a48d8febecd22f600e462bdcdd`
- Tree response: `truncated=false`
- Repository metadata reports MIT license for repository code. Data, model checkpoints, and nested third-party subprojects require separate review.

| Upstream path | Blob SHA | Indexed role |
|---|---|---|
| `LICENSE` | `0e6b144b4bcac3fabddd0d72aa893fc7c50f2fac` | Code license evidence |
| `README.md` | `f318ac182f4ade072678eebf8646a635adfceabf` | Benchmark protocol and project map |
| `baselines/artprompt/artprompt.py` | `8dd4f43c4531fcc5d9c0a252bb2570624e129594` | ArtPrompt baseline |
| `baselines/autoprompt/autoprompt.py` | `1d77a1a54b36ca44f71cba52bf4799cbe60ff6a0` | AutoPrompt baseline |
| `baselines/pair/judges.py` | `0f36931ed90e09354de4e9b5e113eb30285fd1f8` | PAIR judge component |
| `baselines/pair/system_prompts.py` | `2b12e818a6a9e66e28ec3aa06353bb2292967356` | PAIR system prompt source; do not copy executable payloads |
| `baselines/tap/judges.py` | `4e1362a571f0e54a0a2a370034259151fef46a13` | TAP judge component |
| `baselines/tap/system_prompts.py` | `cd9f065bb00119b1aeb9ca5807cd07f3ceba7c63` | TAP system prompt source; do not copy executable payloads |
| `configs/method_configs/ArtPrompt_config.yaml` | `9e2081dd117ef80e433baa0a6b11f47ca111c430` | ArtPrompt configuration |
| `configs/method_configs/AutoPrompt_config.yaml` | `1c5138efb0245d267bd6d5518c453649514b6b00` | AutoPrompt configuration |
| `data/behavior_datasets/harmbench_behaviors_text_all.csv` | `8a6b423d85e9acdc168c57a6a957755cfa86c4cb` | Text behavior dataset; terms review required |
| `data/behavior_datasets/harmbench_behaviors_text_test.csv` | `a150df81f1efa24496f1495e1b96822fd403e339` | Text test split; terms review required |
| `data/behavior_datasets/harmbench_behaviors_text_val.csv` | `0cfc6c419122c58df0ccbda6351c0265dc72b125` | Text validation split; terms review required |
| `data/behavior_datasets/harmbench_behaviors_multimodal_all.csv` | `d39d6c6b4ad68e37e60a408d3181791b49740221` | Multimodal behavior dataset; terms review required |
| `data/classifier_val_sets/text_behaviors_val_set.json` | `3d7d0a98742a36b5c7824aadcea433e42a045022` | Text classifier validation set |
| `data/classifier_val_sets/multimodal_behaviors_val_set.json` | `bcf9fb999bee7c5a3d9018163f8eaa86d2b21ecd` | Multimodal classifier validation set |

## Prompt Injection Detector Benchmark

- Repository: https://github.com/bastion-soft/pi-detector-bench
- Default branch: `main`
- Inspected tree SHA: `fcf543fa9ccb790123173e3d98a149fd5f02c7e5`
- Tree response: `truncated=false`
- Repository metadata reports MIT license. Dataset sources retain their own terms.

| Upstream path | Blob SHA | Indexed role |
|---|---|---|
| `LICENSE` | `a7419715c050b6f74868f068b51c100ad900a6e4` | Code license evidence |
| `METHODOLOGY.md` | `96de4236cbef8f06e12af647cac98e2ffadbfaef` | Threshold-agnostic two-axis evaluation methodology |
| `pidbench/benchmark_suite.py` | `893599960f889a931de36112f09f36f9ebefaa49` | Benchmark orchestration |
| `pidbench/data.py` | `779e4d38557c95db3bd1fe0f9c33fda7b801c807` | Dataset loading |
| `pidbench/indirect_data.py` | `9da7d65220b132f6599d2af5238e1488df21233f` | Indirect-injection dataset adapter |
| `pidbench/multiturn_data.py` | `4c77c80e5d9a36671d710a0012f6641ff26d7850` | Multi-turn dataset adapter |
| `pidbench/metrics.py` | `87c10558040cea15f99f499a882ec747d56147cc` | Detection and false-positive metrics |
| `pidbench/models.py` | `60b7a3acda43e5410f1ecb0f48a9523ac84803a6` | Detector model adapters |
| `pidbench/runners.py` | `211e4db7408ca6ade964dd80f35cae9a892191d4` | Evaluation runners |
| `pidbench/scores_io.py` | `7f22b400b41324b985770f4c742ffdbfcb7b0d4b` | Raw score persistence |
| `results/leaderboard.json` | `01b2d7041bb01f47042ec308da798517df546fb8` | Committed detector score data |
| `results/FINDINGS.md` | `557c40aad5ee3f09c5c74bbd2b7a4fceded6114f` | Interpretation and limitations |

## Follow-up queue

- Continue enumerating all source files, tests, configs, data cards, and release snapshots for each registered repository.
- Add every discovered path to this index or a specialized registry; never silently drop duplicates or older variants.
- Do not treat a tree snapshot as source-code review: fetch and inspect file contents before claiming implementation details.
