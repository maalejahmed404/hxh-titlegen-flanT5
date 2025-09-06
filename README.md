# Hunter × Hunter Episode Title Generation with FLAN-T5

Fine-tuning **FLAN-T5** to generate *Hunter × Hunter* episode titles from long subtitles.  
We overcome the 512-token context limit using a **sliding-window** strategy and, at inference time, we **carry the previously generated title** into the next window’s prompt.

---

## Highlights
- **Model:** `google/flan-t5-base` (seq2seq).
- **Context handling:** 512-token windows with **stride 400**; **previous-title carry-over** at inference.
- **Training data:** 145 episodes → split **125 / 10 / 10** (train / val / test).
- **Label alignment:** train on the **last window(s)** per episode to avoid misleading supervision.
- **Evaluation:** ROUGE (surface overlap) + **BERTScore** (semantic similarity).
- **Outcome:** Fine-tuning converts noisy/base outputs into **short, title-like** strings (Title Case, “X and Y” form). Semantic similarity improves (per-example BERTScore up to ~**60%**), while ROUGE stays modest due to creative targets.

---

## Repo structure
