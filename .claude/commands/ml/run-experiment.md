# Run Experiment

Execute ML training with proper logging and checkpointing.

## Usage
```
/ml/run-experiment [config.yaml]
```

## Workflow

### 1. Pre-flight Checks
```bash
# Check GPU availability
nvidia-smi || echo "No GPU detected"

# Check disk space
df -h .

# Verify config file exists
ls config.yaml
```

### 2. Setup
```bash
# Create output directory
mkdir -p outputs/$(date +%Y%m%d_%H%M%S)

# Activate environment
source venv/bin/activate || conda activate ml
```

### 3. Run Training
```bash
# Standard PyTorch
python train.py --config config.yaml

# With logging
python train.py --config config.yaml 2>&1 | tee outputs/train.log

# With wandb
WANDB_PROJECT=myproject python train.py --config config.yaml
```

### 4. Monitor Progress
```bash
# Watch GPU usage
watch -n 1 nvidia-smi

# Tail log
tail -f outputs/train.log

# TensorBoard
tensorboard --logdir outputs/
```

### 5. Save Results
```bash
# Copy final checkpoint
cp outputs/latest/checkpoint.pt outputs/final/

# Save config with results
cp config.yaml outputs/final/
```

## Config Template

```yaml
# config.yaml
model:
  name: resnet50
  pretrained: true

data:
  train_path: data/train
  val_path: data/val
  batch_size: 32
  num_workers: 4

training:
  epochs: 100
  lr: 0.001
  optimizer: adamw
  scheduler: cosine

logging:
  save_every: 10
  log_every: 100
  output_dir: outputs/
```

## Common Patterns

### Resume from checkpoint
```bash
python train.py --config config.yaml --resume outputs/checkpoint.pt
```

### Multi-GPU
```bash
torchrun --nproc_per_node=4 train.py --config config.yaml
```

### Hyperparameter sweep
```bash
for lr in 0.001 0.0001 0.00001; do
  python train.py --config config.yaml --lr $lr
done
```

## Output Structure

```
outputs/
├── 20240115_143022/
│   ├── config.yaml
│   ├── train.log
│   ├── checkpoints/
│   │   ├── epoch_10.pt
│   │   ├── epoch_20.pt
│   │   └── best.pt
│   ├── tensorboard/
│   └── metrics.json
```
