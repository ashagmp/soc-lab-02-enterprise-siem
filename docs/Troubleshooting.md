````markdown
# Troubleshooting

## Splunk Indexing Paused Due to Low Disk Space

### Problem

Splunk Enterprise reported a critical disk-space warning and paused indexing.

The Splunk Web interface reported that free disk space had fallen below the configured minimum of 5000 MB. Indexing was paused and internal audit events were being dropped.

### Investigation

Checked the root filesystem:

```bash
df -h /
````

Initial state:

| Setting         | Value   |
| --------------- | ------- |
| Filesystem Size | 12 GB   |
| Used            | 11 GB   |
| Available       | ~287 MB |
| Usage           | 98%     |

The VirtualBox virtual disk was then checked and found to have additional unallocated capacity after increasing the virtual disk size.

### Root Cause

The Splunk server was initially provisioned with insufficient storage for the expected SIEM workload.

The VirtualBox virtual disk was expanded from **12 GB to 50 GB**, but the additional capacity was not automatically added to the Ubuntu LVM filesystem.

### Resolution

#### 1. Expand VirtualBox Disk

The `splunk01` virtual disk was expanded from:

```text
12 GB → 50 GB
```

#### 2. Expand the LVM Physical Volume

```bash
sudo pvresize /dev/sda3
```

#### 3. Extend the Logical Volume

```bash
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```

#### 4. Expand the Filesystem

```bash
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

### Verification

Checked the filesystem after the expansion:

```bash
df -h /
```

Final state:

| Setting         | Before  | After |
| --------------- | ------- | ----- |
| Filesystem Size | 12 GB   | 23 GB |
| Available Space | ~287 MB | 12 GB |
| Usage           | 98%     | 49%   |

The Splunk Web disk-space warning subsequently cleared and indexing resumed normally.

### Result

Splunk Enterprise recovered successfully after additional storage was allocated to the Ubuntu filesystem.

### Lessons Learned

* SIEM infrastructure requires sufficient storage capacity.
* Virtual disk expansion does not automatically expand the guest OS filesystem.
* LVM and the filesystem must be expanded after increasing the virtual disk.
* Disk capacity should be monitored before adding additional log sources.
* Service health should be verified after resolving infrastructure issues.

```
```
