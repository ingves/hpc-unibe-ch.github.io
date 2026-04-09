# Pay-as-you-go (PAYGO) Scheme

The PAYGO model on UBELIX provides flexible, usage-based billing for HPC resources. It’s ideal for users with sporadic or changing workloads. With PAYGO, you only pay for the actual resources you use - there are no upfront payments or long-term commitments.

!!! tip "Debug & Preemptable Jobs"
    Jobs running in **debug** or **preemptable** QOS are **not billed**, allowing you to test and benchmark your code efficiently before committing to longer runs.

## How Pricing Works

- **CPU Nodes:**
  Both CPU and memory usage are billed. Memory is converted to CPU-equivalents for pricing. For example:
  On a node with 128 cores and 1TB of memory, if you use 512GB of memory, you are billed for 64 CPUs, regardless of how many CPUs you actually requested (as long as your CPU request is 64 or less). On the other hand, if you request 72 CPUs and 20GB of memory on the same node, you are billed for 72 CPUs, regardless of the memory you requested. The cost is calculated using the higher value between CPUs and memory used: `max(cpu, mem)`.

- **GPU Nodes:**
  Only GPU usage is billed. CPU and memory use on GPU nodes are not charged separately.

You can always check the latest prices [here](https://intern.unibe.ch/dienstleistungen/informatik/dienstleistungen_der_informatikdienste/dienstleistungen___ressourcen/high_performance_computing___hpc___grid/index_ger.html#tab-pane-3) (internal access or UniBE-VPN required).

!!! success "OPEX Coverage"
    All operational and network costs (such as hardware, licenses, and staff) are covered by **central IT services**.
    This means that **100% of your payments are reinvested into new compute hardware for UBELIX users.**


### UBELIX vs. Cloud Providers

UBELIX offers significantly lower prices than commercial cloud providers—and your bill includes storage, network traffic, and managed software support.

### Research Group / Project Free Tier

PAYGO projects are supported by central IT Services with an annual support credit of **up to CHF 1,000 per cost center**. This credit is intended to help research groups cover costs and to support exploratory work with limited financial risk.

The credit is awarded once per fiscal year and is applied **per cost center**. If multiple PAYGO projects use the same cost center, they all draw from the same annual credit limit.

All monthly PAYGO invoices must be paid in full when due. The support credit is then reimbursed automatically **at the end of the fiscal year** through an internal transfer to the cost center. No action is required from the user.

**Examples**:

  - If a cost center incurs CHF 800 in PAYGO charges during the year, it receives a refund of CHF 800.
  - If a cost center incurs CHF 1,500 in PAYGO charges during the year, it receives the maximum refund of CHF 1,000.

!!! danger "Warning"

    This credit is granted only once per cost center each fiscal year. If the free tier is misused, we may discontinue it.

## Using PAYGO in Practice

- Projects are created and managed in the IAM portal by [institute technology managers](https://intern.unibe.ch/dienstleistungen/informatik/dienstleistungen_der_informatikdienste/it_verantwortliche/index_ger.html). Managers can appoint project administrator delegates to help manage project members [(details)](https://serviceportal.unibe.ch/esc?id=kb_article_view&sys_kb_id=d6dbd470473b3a904fb1438c736d4306) 
- Project members are users authorized to use the project’s resources. Every project has a unique identifier ("wckey") that links users to the project.
- When creating a project, a valid credit number and cost limit must be set.
- To submit a job using PAYGO:
    - Select the paygo account: `--account=paygo`
    - Specify your project’s wckey: `--wckey=<wckey>`
- Only jobs submitted with the paygo account and a valid wckey will incur costs.
- Each month, UBELIX sends a bill to the credit number associated with your project.

### Notes

- Users can belong to multiple projects and use the relevant wckey for each job.
- You can specify a wckey with the invest or gratis account as well. In these cases, no costs are charged, but the project's resource usage is tracked - helpful for understanding the true cost, even if it isn’t billed.

