# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          #  - public_repo
          #  - read:project
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: Kaiasaurin
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: America/Los_Angeles
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_analysis_timeout_repositories: 7.5
          plugin_languages_categories: programming
          plugin_languages_colors: github
          plugin_languages_ignored: css
          plugin_languages_limit: 8
          plugin_languages_recent_categories: programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_notable: yes
          plugin_notable_from: all
          plugin_notable_repositories: yes
          plugin_notable_self: yes
          plugin_notable_types: commit
          plugin_projects: yes
          plugin_projects_limit: 3
