# git_assignment_HeroVired

This repository contains the solutions for the Git assignment from HeroVired. The assignment covers various Git concepts including branching, merging, pull requests, Git LFS, and Git stash.



## Assignment Description

This assignment focuses on demonstrating proficiency in Git and GitHub workflows. It involves implementing new features, managing branches, handling large files, and utilizing Git stash for efficient development


## Task 1: CalculatorPlus Application - Git Workflow

This task involves implementing a new square root feature in a Python calculator application and demonstrating various Git branching and merging strategies, including handling a critical bug fix.

### Steps Performed

1.  **Repository Creation (a):**
    * Created a new private GitHub repository named `git_assignment_HeroVired`.
    * Initialized with a `README.md` file.

2.  **`dev` Branch Creation and Initial Code (b):**
    * Cloned the repository to the local machine: `git clone <repository_url>`
    * Created a new branch named `dev`: `git checkout -b dev`
    * Created a `calculator.py` file with the provided initial code:
        ```python
        import math

        class Calculator:
            def add(self, a, b):
                return a + b

            def subtract(self, a, b):
                return a - b

            def multiply(self, a, b):
                return a * b

            def divide(self, a, b):
                return a / b

            # TODO: Implement the following function to calculate the square root of a number.
            # def square_root(self, x):
            # return math.sqrt(x)

        if __name__ == "__main__":
            calculator = Calculator()
            num1 = 16
            num2 = 4
            print(f"{num1} + {num2} = {calculator.add(num1, num2)}")
            print(f"{num1} - {num2} = {calculator.subtract(num1, num2)}")
            print(f"{num1} * {num2} = {calculator.multiply(num1, num2)}")
            print(f"{num1} / {num2} = {calculator.divide(num1, num2)}")

            # TODO: Uncomment and test the square root feature.
            # num3 = 25
            # print(f"The square root of {num3} = {calculator.square_root(num3)}")
        ```
    * Staged and committed the changes: `git add calculator.py` and `git commit -m "Initial CalculatorPlus application on dev branch"`
    * Pushed the `dev` branch to GitHub: `git push -u origin dev`

3.  **Merge to `main` and Release v1 (c):**
    * Switched to the `main` branch: `git checkout main`
    * Merged the `dev` branch into `main`: `git merge dev`
    * Pushed the `main` branch to GitHub: `git push origin main`
    * Created a release tag `v1.0.0` for "Version 1 of Calculator Plus App" on GitHub.

4.  **Add Collaborators (d):**
    * (Not directly performable via Git commands, but simulated steps)
    * Navigated to the GitHub repository settings.
    * Went to "Collaborators and teams" and added a dummy collaborator (or described the process if a real classmate was not available at the moment).

5.  **Create `feature/sqrt` Branch (e):**
    * Switched back to the `dev` branch: `git checkout dev`
    * Created a new branch for the square root feature: `git checkout -b feature/sqrt`

6.  **Implement Square Root Feature (f):**
    * Modified `calculator.py` to uncomment and complete the `square_root` function:
        ```python
        import math

        class Calculator:
            # ... existing methods ...
            def square_root(self, x):
                if x < 0:
                    raise ValueError("Cannot calculate square root of a negative number.")
                return math.sqrt(x)

            # ... existing __main__ block ...
        ```
    * Uncommented and added the test for `square_root` in the `if __name__ == "__main__":` block:
        ```python
        # ... existing tests ...
        num3 = 25
        print(f"The square root of {num3} = {calculator.square_root(num3)}")
        ```
    * Staged the changes: `git add calculator.py`
    * (Did *not* commit yet, as the next step involves an interruption.)

7.  **Critical Bug Fix and `feature/sqrt` Update (g):**
    * **Switch to `dev`:** `git checkout dev`
    * **Create `fix/divide-by-zero` branch:** `git checkout -b fix/divide-by-zero`
    * **Implement bug fix in `calculator.py`:**
        ```python
        class Calculator:
            # ...
            def divide(self, a, b):
                if b == 0:
                    raise ValueError("Cannot divide by zero.")
                return a / b
            # ...
        ```
    * Staged and committed the fix: `git add calculator.py` and `git commit -m "FIX: Handle divide by zero error"`
    * **Merge `fix/divide-by-zero` into `dev`:**
        * `git checkout dev`
        * `git merge fix/divide-by-zero`
        * `git branch -d fix/divide-by-zero` (delete the fix branch)
        * `git push origin dev`
    * **Update `feature/sqrt` with `dev` changes:**
        * `git checkout feature/sqrt`
        * `git merge dev` (or `git rebase dev` for a cleaner history if preferred, but `merge` is simpler here)
        * Resolved any potential merge conflicts (none expected in this specific scenario).
        * Staged and committed the merge result if conflicts occurred.
        * Pushed the `feature/sqrt` branch to GitHub: `git push -u origin feature/sqrt`

8.  **Create Pull Request (h):**
    * Navigated to GitHub.
    * Created a new pull request from `feature/sqrt` to `main` branch.
    * Provided a descriptive title and description (e.g., "Feature: Implement Square Root Functionality").

9.  **Request Code Review and Improvements (i):**
    * Requested a code review from the designated collaborator (or described this step in the PR description).
    * (Simulated receiving feedback and making minor improvements if necessary, committing and pushing them to `feature/sqrt`).

10. **Merge `feature/sqrt` to `dev` (j):**
    * (Assumed code review approval on GitHub PR)
    * Switched to the `dev` branch: `git checkout dev`
    * Merged `feature/sqrt` into `dev`: `git merge feature/sqrt`
    * Pushed the `dev` branch to GitHub: `git push origin dev`
    * Deleted the `feature/sqrt` branch locally: `git branch -d feature/sqrt`
    * Deleted the `feature/sqrt` branch on remote: `git push origin --delete feature/sqrt`

11. **Testing in `dev`, Merge to `main`, and Release v2 (k):**
    * Performed local testing on the `dev` branch to ensure all features (addition, subtraction, multiplication, safe division, square root) work correctly.
        * Ran `python calculator.py` and verified outputs.
        * Tested `calculator.divide(10, 0)` to ensure `ValueError` is raised.
    * Switched to the `main` branch: `git checkout main`
    * Merged the `dev` branch into `main`: `git merge dev`
    * Pushed the `main` branch to GitHub: `git push origin main`
    * Created a new release tag `v2.0.0` for "Version 2 of Calculator Plus App with Square Root and Bug Fix" on GitHub.

---

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

---

## Task 3: Geometry Calculator - Git Stash Workflow

This task demonstrates using Git stash to manage incomplete changes when switching between multiple feature implementations.

### Steps Performed

1.  **Create `geometry-calculator` Branch:**
    * Switched to the `dev` branch: `git checkout dev`
    * Created a new branch named `geometry-calculator`: `git checkout -b geometry-calculator`
    * Created `geometry_calculator.py` with the provided initial code:
        ```python
        import math

        class GeometryCalculator:
            def calculate_circle_area(self, radius):
                return math.pi * radius ** 2

            def calculate_rectangle_area(self, length, width):
                return length * width

        if __name__ == "__main__":
            calculator = GeometryCalculator()
            # TODO: Implement the feature to calculate the area of a circle
            # radius = 5
            # print(f"The area of the circle with radius {radius} = {calculator.calculate_circle_area(radius)}")
            # TODO: Implement the feature to calculate the area of a rectangle
            # length = 10
            # width = 6
            # print(f"The area of the rectangle with length {length} and width {width} = {calculator.calculate_rectangle_area(length, width)}")
        ```
    * Committed this initial file: `git add geometry_calculator.py` and `git commit -m "Initial Geometry Calculator setup"`
    * Pushed the branch: `git push -u origin geometry-calculator`

2.  **Create `feature/circle-area` Branch (a):**
    * From `geometry-calculator` branch: `git checkout -b feature/circle-area`

3.  **Start Circle Area Feature Implementation:**
    * Modified `geometry_calculator.py` to uncomment the circle area part:
        ```python
        # ...
        if __name__ == "__main__":
            calculator = GeometryCalculator()
            # TODO: Implement the feature to calculate the area of a circle
            radius = 5
            print(f"The area of the circle with radius {radius} = {calculator.calculate_circle_area(radius)}")
            # TODO: Implement the feature to calculate the area of a rectangle
            # length = 10
            # width = 6
            # print(f"The area of the rectangle with length {length} and width {width} = {calculator.calculate_rectangle_area(length, width)}")
        ```
    * Staged the changes: `git add geometry_calculator.py`

4.  **Stash Changes for Circle Area Feature (b):**
    * Stashed the incomplete changes: `git stash save "Incomplete circle area feature"`
    * Verified the working directory is clean: `git status` (should show a clean working tree)

5.  **Create `feature/rectangle-area` Branch (c):**
    * Switched back to `geometry-calculator` (or `dev` if preferred, but `geometry-calculator` is fine here as a base): `git checkout geometry-calculator`
    * Created a new branch for the rectangle area feature: `git checkout -b feature/rectangle-area`

6.  **Start Rectangle Area Feature Implementation:**
    * Modified `geometry_calculator.py` to uncomment the rectangle area part:
        ```python
        # ...
        if __name__ == "__main__":
            calculator = GeometryCalculator()
            # TODO: Implement the feature to calculate the area of a circle
            # radius = 5
            # print(f"The area of the circle with radius {radius} = {calculator.calculate_circle_area(radius)}")
            # TODO: Implement the feature to calculate the area of a rectangle
            length = 10
            width = 6
            print(f"The area of the rectangle with length {length} and width {width} = {calculator.calculate_rectangle_area(length, width)}")
        ```
    * Staged the changes: `git add geometry_calculator.py`

7.  **Stash Changes for Rectangle Area Feature (d):**
    * Stashed the incomplete changes: `git stash save "Incomplete rectangle area feature"`
    * Verified the working directory is clean: `git status`

8.  **Switch Back to Circle Area Branch and Complete (e):**
    * Switched back to `feature/circle-area`: `git checkout feature/circle-area`
    * Retrieved the stashed changes: `git stash pop` (or `git stash apply` followed by `git stash drop`)
    * Ensured `geometry_calculator.py` is fully implemented for circle area (no further code changes needed based on the provided snippet, as it was just uncommenting).
    * Verified functionality locally: `python geometry_calculator.py`

9.  **Commit and Push Circle Area Feature (f):**
    * Committed the completed feature: `git commit -m "FEAT: Implement circle area calculation"`
    * Pushed the branch: `git push -u origin feature/circle-area`

10. **Switch Back to Rectangle Area Branch and Complete (g):**
    * Switched back to `feature/rectangle-area`: `git checkout feature/rectangle-area`
    * Retrieved the stashed changes: `git stash pop`
    * Ensured `geometry_calculator.py` is fully implemented for rectangle area.
    * Verified functionality locally: `python geometry_calculator.py`

11. **Commit and Push Rectangle Area Feature (h):**
    * Committed the completed feature: `git commit -m "FEAT: Implement rectangle area calculation"`
    * Pushed the branch: `git push -u origin feature/rectangle-area`

12. **Create Pull Requests (i):**
    * Navigated to GitHub.
    * Created a pull request from `feature/circle-area` to `dev` branch.
    * Created a pull request from `feature/rectangle-area` to `dev` branch.

13. **Review and Merge (j):**
    * (Simulated team member review and approval for both PRs.)
    * On GitHub, merged the `feature/circle-area` PR into `dev`.
    * On GitHub, merged the `feature/rectangle-area` PR into `dev`.
    * (Locally, pulled `dev` to update `git checkout dev` then `git pull origin dev`)
    * (Optionally, delete feature branches locally and remotely after merging: `git branch -d feature/circle-area`, `git push origin --delete feature/circle-area`, etc.)
    * Finally, merged the `dev` branch into `main` (if all features are considered stable for production): `git checkout main` and `git merge dev`.
    * Pushed the `main` branch: `git push origin main`.
