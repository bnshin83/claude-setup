# Analyze Results

Parse and summarize ML experiment results.

## Usage
```
/ml/analyze-results [output_dir]
```

## Workflow

### 1. Find Results
```bash
# List recent experiments
ls -lt outputs/ | head -10

# Find best checkpoint
find outputs/ -name "best*.pt" -o -name "*best*"
```

### 2. Parse Metrics
```python
# Read metrics from JSON
import json
with open("outputs/metrics.json") as f:
    metrics = json.load(f)

# Read from CSV
import pandas as pd
df = pd.read_csv("outputs/metrics.csv")
```

### 3. Extract Key Results

```markdown
## Experiment Summary

### Configuration
- Model: ResNet50
- Dataset: CIFAR-10
- Epochs: 100
- Learning rate: 0.001

### Results
| Metric | Train | Val | Test |
|--------|-------|-----|------|
| Accuracy | 99.2% | 95.3% | 94.8% |
| Loss | 0.023 | 0.187 | 0.201 |

### Training Curve
- Best epoch: 87
- Early stopped: No
- Total time: 4h 23m

### Observations
- Slight overfitting after epoch 70
- Validation accuracy plateaued at epoch 85
```

### 4. Compare Experiments

```bash
# Compare multiple runs
for dir in outputs/exp_*; do
  echo "=== $dir ==="
  cat "$dir/metrics.json" | jq '.best_val_acc'
done
```

## Quick Analysis Scripts

### Find best run
```python
import os
import json

results = []
for exp in os.listdir("outputs"):
    metrics_path = f"outputs/{exp}/metrics.json"
    if os.path.exists(metrics_path):
        with open(metrics_path) as f:
            m = json.load(f)
            results.append((exp, m.get("best_val_acc", 0)))

results.sort(key=lambda x: x[1], reverse=True)
print("Top 5 runs:")
for name, acc in results[:5]:
    print(f"  {name}: {acc:.4f}")
```

### Plot training curves
```python
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv("outputs/metrics.csv")
plt.figure(figsize=(10, 4))

plt.subplot(1, 2, 1)
plt.plot(df["epoch"], df["train_loss"], label="Train")
plt.plot(df["epoch"], df["val_loss"], label="Val")
plt.xlabel("Epoch")
plt.ylabel("Loss")
plt.legend()

plt.subplot(1, 2, 2)
plt.plot(df["epoch"], df["train_acc"], label="Train")
plt.plot(df["epoch"], df["val_acc"], label="Val")
plt.xlabel("Epoch")
plt.ylabel("Accuracy")
plt.legend()

plt.savefig("training_curves.png")
```

## Output Format

```markdown
## Analysis: outputs/20240115_143022

### Quick Stats
- Final val accuracy: 95.3%
- Best val accuracy: 95.8% (epoch 87)
- Training time: 4h 23m
- GPU memory peak: 12.4 GB

### Hyperparameters
- lr: 0.001
- batch_size: 32
- optimizer: AdamW
- scheduler: CosineAnnealingLR

### Files
- Best checkpoint: outputs/20240115_143022/checkpoints/best.pt
- Final checkpoint: outputs/20240115_143022/checkpoints/epoch_100.pt
- Metrics: outputs/20240115_143022/metrics.json
- Logs: outputs/20240115_143022/train.log

### Recommendations
- Model achieved good performance
- Consider reducing LR for fine-tuning
- Try data augmentation for better generalization
```
