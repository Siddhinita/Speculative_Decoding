# Speculative_Decoding

The colab contains a basic implementation of speculative decoding using Qwen models. Specifically, it utilizes `Qwen/Qwen2.5-1.5B-Instruct` as the teacher model and `Qwen/Qwen2.5-0.5B-Instruct` as the drafter model.

### Overview & Performance

Roughly speaking, the output quality of this speculative decoding setup successfully matches the teacher model while outperforming the standalone drafter model. Based on a 50-question evaluation subset:
* **Teacher Model (`Qwen 1.5B`):** Achieved an accuracy of 36.0%.
* **Drafter Model (`Qwen 0.5B`):** Achieved an accuracy of 26.0%.
* **Speculative Decoding:** Matched the teacher model with an accuracy of 36.0%.

### Current Limitations

* **Latency:** Because this is a synchronous (sync) implementation, the execution pipeline creates a bottleneck, meaning we do not see the latency savings typically associated with speculative decoding. Currently, the average time per token for the speculative decoding implementation is ~0.245s, which is slower than the teacher model's ~0.085s.

## TODO

- [ ] Measure and update the acceptance rates of the drafter model's tokens.
- [ ] Add comprehensive speculative decoding metrics (e.g., token-per-second generation rates, latency profiles, etc.).
- [ ] Optimize the pipeline to an asynchronous workflow to unlock actual latency savings.
