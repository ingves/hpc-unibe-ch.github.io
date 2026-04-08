# Free tiers
To maintain accessibility for all users, UBELIX provides **three free-tier levels**.
These ensure that unfunded projects, students, and small groups can still perform meaningful computation.

## F1 - User Free-Tier

Every UBELIX user automatically receives access to the F1 Free-Tier, designed for getting started, coursework, debugging, or running short simulations.

### What You Get

#### CPU Access

- 11520 TRES run minutes
    -  This is equivalent to approximately 24 hours of compute time on 8 CPU cores.
    -  **TRES** stands for "Trackable Resources," which UBELIX uses to measure and manage your resource usage.
    - For example, if you run a job with 8 CPU cores for 3 hours (180 minutes), you will use up 1440 TRES minutes (8 cores × 180 minutes).
    - If you run a job with 1 CPU core for 10 hours (600 minutes), you will use 600 TRES minutes (1 core × 600 minutes).
    - If you run a job with 4 CPU cores for 6 hours (360 minutes), that’s 1440 TRES minutes (4 × 360 minutes).

!!! note "Important"
    The 11520 TRES minute limit applies to the total *simultaneously* used TRES minutes at any one time. This means the system tracks the sum of all your active jobs, and as soon as a job finishes, those TRES minutes are immediately freed and your allowance resets accordingly. You can start new jobs as soon as previous ones complete, as long as you never exceed the simultaneous usage cap.

You can submit more jobs than your current TRES minute limit allows. If you do, these jobs will remain in the queue and will start automatically once enough TRES minutes become available (for example, when active jobs finish and free up capacity).

#### GPU Access

  - Up to **2× RTX 4090 GPUs** (from a shared pool of 16 GPUs)
  - Up to **1× H100 GPU** (from a shared pool of 8 GPUs)

These GPUs are available for your jobs in the free tier, but because the pools are shared, availability may depend on current demand.

### Use Cases

This tier is ideal for:

- Running coursework assignments or learning how to use UBELIX
- Debugging scripts and code before scaling up
- Short or exploratory simulations
- Testing resource requirements before submitting larger jobs

### Important Notes

- Free-tier usage is tracked per user and resets as jobs finish.
- Jobs submitted beyond your simultaneous TRES minute limit will be held in the queue until resources become available.
- If your free-tier becomes too restrictive to your workflow, you’ll need to use the "paygo" account of a PAYGO project or investment account to submit more resource intensive jobs.
- Resource availability (especially GPUs) may vary depending on overall system usage.

## F2 - Research Group / Project Free Tier

PAYGO projects are supported by central IT Services with an annual support credit of **up to CHF 1,000 per cost center**. This credit is intended to help research groups cover costs and to support exploratory work with limited financial risk.

The credit is awarded once per fiscal year and is applied **per cost center**. If multiple PAYGO projects use the same cost center, they all draw from the same annual credit limit.

All monthly PAYGO invoices must be paid in full when due. The support credit is then reimbursed automatically **at the end of the fiscal year** through an internal transfer to the cost center. No action is required from the user.

**Examples**:

  - If a cost center incurs CHF 800 in PAYGO charges during the year, it receives a refund of CHF 800.
  - If a cost center incurs CHF 1,500 in PAYGO charges during the year, it receives the maximum refund of CHF 1,000.

!!! danger "Warning"

    This credit is granted only once per cost center each fiscal year. If the free tier is misused, we may discontinue it.


## F3 - Preemptable Tier

UBELIX maximizes hardware utilization by making unused investor resources available as **preemptable compute slots**.

- **What are Preemptable Slots?**
  - These are free compute resources available to any UBELIX user when investor-owned hardware is idle.
  - Jobs running in preemptable slots can be interrupted ("preempted") at any time if the resource owner submits new jobs that require those resources.
  - This model allows opportunistic computing: you get free access to powerful hardware, but with the risk of interruption.

!!! warning "Recommendation"
    Use **checkpointing** when running preemptable jobs to avoid losing progress or data if your job is interrupted.

- **Use Cases:**
  - Suitable for non-urgent jobs, exploratory work, large parameter sweeps, or workloads designed to restart from checkpoints.
  - Not recommended for critical workloads unless they are checkpoint-enabled.

## How Free-Tier Resources Work in Practice

- The **F1 User Free-Tier** is the default for all users and is associated with the **gratis** account.
- You can use free-tier resources even if you are also associated with a cost-enabled PAYGO-project.
- You may associate a job with a PAYGO project by specifying its wckey, even when using the free-tier. This allows you to track usage for project reporting without incurring any costs.
- The following Quality of Service (QOS) levels are enabled for gratis account jobs:
    - `job_gratis`: Standard free-tier jobs (F1)
    - `job_cpu_preemptable`: Access to preemptable CPU resources (F3)
    - `job_gpu_preemptable`: Access to preemptable GPU resources (F3)
    - `job_debug`: Short, quick jobs for debugging and testing

