# MyGet Mirror (Mediaportal)

This repository serves as an automated mirror for the [Mediaportal MyGet V3 feed](https://www.myget.org/F/mediaportal/api/v3/index.json). It ensures that all verified packages from the original feed are available as **GitHub Packages**.

## 🚀 Usage

To use these packages in your project, add the GitHub NuGet source to your `nuget.config`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <packageSources>
    <add key="TeamMediaPortal @ GitHub" value="https://nuget.pkg.github.com/Mediaportal-Plugin-Team/index.json" />
  </packageSources>
</configuration>
```

> **Note:** Accessing GitHub Packages requires a Personal Access Token (PAT) with at least `read:packages` scope.

## 🛠 How it Works

The mirroring process is automated via **GitHub Actions**:

*   **Frequency:** Runs daily at midnight (UTC) or can be triggered manually.
*   **Discovery:** Scans the MyGet V3 Search Service for all `verified` packages.
*   **Efficiency:** Uses a "Download-and-Push" strategy with `--skip-duplicate` handling to ensure fast updates without redundant operations.
*   **Source:** All packages are fetched directly from the [Mediaportal MyGet Feed](https://www.myget.org/F/mediaportal/api/v3/index.json).

## 📂 Repository Structure

*   `.github/workflows/sync.yml`: The PowerShell-based GitHub Action that performs the sync.
*   `LICENSE`: Licensed under the **AGPL-3.0**.

## 📝 Maintenance

This repository is maintained by the **Mediaportal-Plugin-Team**. If you find any issues with the synchronization, please open an issue in this repository.

