### Storage Types: Block Storage and File Storage
![Screenshot from 2024-02-02 11-05-04](https://github.com/ishtiaqSamdani/gcp/assets/82057297/fc284d1f-a71f-48f8-80ba-781044b1c4b3)

1. **Hard Disk Type:**
   - Your hard disk uses **Block Storage.**

2. **File Share in Enterprise:**
   - When creating a file share for colleagues in an enterprise, you are using **File Storage.**

### GCP - Block Storage and File Storage

#### Block Storage:

3. **Persistent Disks:**
   - Network Block Storage.
   - Zonal: Data replicated in one zone.
   - Regional: Data replicated in multiple zones.

4. **Local SSDs:**
   - Physically attached to the VM host.
   - Temporary data with a lifecycle tied to VM instance.

#### Local SSDs:
   - Advantages and Disadvantages:
     - **Advantages:**
       - Very fast I/O.
       - Ideal for high IOPs and temporary storage (e.g., caches).
     - **Disadvantages:**
       - Ephemeral storage with lower durability, availability, and flexibility.

#### Network Block Storage (Persistent Disks):

5. **Provisioned Capacity:**
   - Very flexible, allowing size adjustments when attached to VM instances.
   - Performance scales with size.
   - Independent lifecycle from VM instances.

6. **Options:**
   - Regional and Zonal PDs (Persistent Disks).
   - Zonal PDs replicated in a single zone, regional PDs in 2 zones in the same region.

7. **Use Case:**
   - Suitable for running custom databases.

### Persistent Disks vs Local SSDs
![Screenshot from 2024-02-02 11-05-59](https://github.com/ishtiaqSamdani/gcp/assets/82057297/1863797b-9891-443b-860b-7df8d8b0ad9a)

8. **Persistent Disks:**
   - Attached as a network drive.
   - Lifecycle separate from VM instance.
   - Suitable for permanent storage.

9. **Local SSDs:**
   - Physically attached.
   - Lifecycle tied to VM instance.
   - Suitable for ephemeral storage.

### Persistent Disks - Standard vs Balanced vs SSD
![Screenshot from 2024-02-02 11-06-27](https://github.com/ishtiaqSamdani/gcp/assets/82057297/cd3f1ff7-8158-4168-9d95-e2b6d84bd788)

10. **Standard, Balanced, SSD:**
   - Differ in underlying storage (HDD, SSD).
   - pd-standard, pd-balanced, pd-ssd respectively.
   - Vary in cost, performance for different use cases.

### Persistent Disks - Snapshots

11. **Snapshot Features:**
   - Point-in-time snapshots of Persistent Disks.
   - Scheduled snapshots with configurable options.
   - Incremental snapshots, shareable across projects.

12. **Best Practices:**
   - Avoid frequent snapshots for performance reasons.
   - Schedule snapshots during off-peak hours.
   - Create images from snapshots for faster disk creation.
   - Organize disks for better snapshot and image management.

13. **Recommendations:**
   - Don't hesitate to delete unnecessary snapshots.
   - Deleting a snapshot only removes data not needed by other snapshots.
