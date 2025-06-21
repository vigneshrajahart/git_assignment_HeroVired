## Task 2: Git LFS Integration

This task demonstrates the integration of Git Large File Storage (LFS) to handle large binary files efficiently within the repository.

### Steps Performed

1.  **Create `lfs` Branch:**
    * Switched to the `main` branch: `git checkout main`
    * Created a new branch named `lfs`: `git checkout -b lfs`

2.  **Install Git LFS (if not already installed):**
    * Ran `git lfs install` (this is a one-time setup on the machine).

3.  **Track Large Files with Git LFS:**
    * Selected a large dummy file (e.g., created a large file using `fallocate -l 250M large_file.bin` on Linux/macOS or a dummy file generator) whose size is over 200MB.
    * Told Git LFS to track files with a specific extension (e.g., `.bin` for binary files): `git lfs track "*.bin"`
    * Verified that `.gitattributes` was created/updated: `git add .gitattributes`
    * Committed `.gitattributes`: `git commit -m "Configure Git LFS to track .bin files"`

4.  **Add, Commit, and Push Large File:**
    * Copied the large file (`large_file.bin`) into the repository.
    * Staged the large file: `git add large_file.bin`
    * Committed the large file: `git commit -m "Add large_file.bin tracked by Git LFS"`
    * Pushed the `lfs` branch to GitHub: `git push -u origin lfs`
    * Verified on GitHub that the file is tracked by LFS (a small pointer file is shown, not the full binary).

5.  **Verify LFS on Another Machine:**
    * (Simulated the process of cloning on another machine)
    * On a different machine (or after deleting the local clone and re-cloning):
        * Cloned the repository: `git clone <repository_url>`
        * Navigated into the `lfs` branch: `git checkout lfs`
        * Verified that `large_file.bin` was downloaded correctly as the actual large file, not just the pointer, by checking its size and content. `ls -lh large_file.bin`