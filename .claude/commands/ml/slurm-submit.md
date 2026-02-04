# SLURM Submit

Submit jobs to SLURM cluster.

## Usage
```
/ml/slurm-submit [script.py] [--partition gpu] [--time 24:00:00]
```

## Quick Submit

### GPU Job
```bash
sbatch <<EOF
#!/bin/bash
#SBATCH --job-name=train
#SBATCH --partition=gpu
#SBATCH --gres=gpu:1
#SBATCH --time=24:00:00
#SBATCH --mem=32G
#SBATCH --cpus-per-task=8
#SBATCH --output=logs/%j.out
#SBATCH --error=logs/%j.err

source ~/.bashrc
conda activate ml
python train.py --config config.yaml
EOF
```

### CPU Job
```bash
sbatch <<EOF
#!/bin/bash
#SBATCH --job-name=preprocess
#SBATCH --partition=cpu
#SBATCH --time=4:00:00
#SBATCH --mem=64G
#SBATCH --cpus-per-task=16
#SBATCH --output=logs/%j.out

python preprocess.py
EOF
```

## SLURM Script Template

```bash
#!/bin/bash
#SBATCH --job-name=experiment
#SBATCH --partition=gpu
#SBATCH --nodes=1
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=8
#SBATCH --gres=gpu:1
#SBATCH --mem=32G
#SBATCH --time=24:00:00
#SBATCH --output=logs/%j_%x.out
#SBATCH --error=logs/%j_%x.err
#SBATCH --mail-type=END,FAIL
#SBATCH --mail-user=you@email.com

# Setup
echo "Job started at $(date)"
echo "Running on $(hostname)"
echo "GPU: $CUDA_VISIBLE_DEVICES"

# Environment
source ~/.bashrc
conda activate ml

# Run
python train.py --config $1

echo "Job finished at $(date)"
```

## Monitoring Commands

```bash
# Check queue
squeue -u $USER

# Job details
scontrol show job <jobid>

# Cancel job
scancel <jobid>

# Cancel all your jobs
scancel -u $USER

# Check cluster status
sinfo

# View job output
tail -f logs/<jobid>.out
```

## Multi-GPU Job

```bash
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=4
#SBATCH --gres=gpu:4

srun python -m torch.distributed.launch \
  --nproc_per_node=4 \
  train.py --config config.yaml
```

## Array Job (Hyperparameter Sweep)

```bash
#SBATCH --array=0-9

# Read hyperparameters from file
LR=$(sed -n "${SLURM_ARRAY_TASK_ID}p" learning_rates.txt)
python train.py --lr $LR
```

## Tips

1. **Always test locally first**: Run for 1 epoch before submitting
2. **Use checkpointing**: Jobs can be preempted
3. **Request appropriate resources**: Don't over-request
4. **Create logs directory**: `mkdir -p logs` before submitting
5. **Use job arrays**: For hyperparameter sweeps
