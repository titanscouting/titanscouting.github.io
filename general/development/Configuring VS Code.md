---
permalink: /general/development/vs-code-docker
title: 2. Configuring VS Code
sort: 2
---

# Configuring VSCode
You must install the VSCode "Remote - Containers" extension to enable development in Docker containers. 

1. Open VS Code.
2. Press "Ctrl-Shift-X" to open the Extensions panel. 
3. In the search box, type "Remote - Containers".
4. Click "Install" on the extension.

## Opening the application in the container
1. Open the cloned repository in VS Code (File > Open Folder).
2. A notification should appear prompting you to open in a Dev Container. Click "Clone in Volume".
3. Press "Enter" to confirm the repository.
4. Click "Create a new volume".
5. Press "Enter" to confirm the volume name.
6. Press "Enter" to confirm the target folder name.
7. The repsitory should now open in the container.
    - If prompted by Windows Defender Firewall, click "Allow access".
    - If, after cloning, you see many changes in Git, discard them. The only difference is the line endings. 

**Please Note: Any non-pushed changes before closing the VS Code window will be lost. Make sure to commit and push your changes before exiting.**
