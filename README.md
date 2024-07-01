# MyHealthBuddy-System
name: Create Release

on:
  push:
    branches:
      - main

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Git
        run: |
          git config user.name "github-actions"
          git config user.email "github-actions@github.com"

      - name: Create Tag
        run: |
          VERSION=$(date +'%Y%m%d%H%M%S')
          git tag -a v$VERSION -m "Automated release for version $VERSION"
          git push origin --tags
