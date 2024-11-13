<p>
  <a href="https://godotengine.org/download">
	<img alt="Godot Download badge" src="https://img.shields.io/badge/godot-4.3-blue">
  </a>
</p>

**Acagamics Godot Game Template** is a generic starter project to allow for quick setup of Gamejam Games. In principle it provides a solid basis to extend on and only covers parts that should be fairly general. Further it provides tools for continuous integration, meaning once something is pushed to the main branch, it automatically generates a windows, linux, and a web export. The latter can be hosted on a Github Pages page or automatically be uploaded to itch.io (untested).


# Get started

You have 2 options:

## 1. Get started with Github Templates:

1. [Create a new repo using this template](https://github.com/ADockhorn/Acagamics-Godot-Game-Template/generate), select to copy all branches 
2. For continuous integration :
  - Github: (1) go to Settings -> Actions -> General and select "Read and write permissions" in the section "Workflow Permissions", (2) go to Settings -> Pages and select "Deploy from a branch" -> gh-pages
3. Clone the new repository locally
4. Open the project in [Godot](https://godotengine.org/download/) (GDScript)

## 2. Get started with a local project:

1. Go to [https://github.com/ADockhorn/Acagamics-Godot-Game-Template](https://github.com/ADockhorn/Acagamics-Godot-Game-Template)
2. Download _Source code (zip)_
3. Unzip the project
4. Open the project in [Godot Engine](https://godotengine.org/download/) (GDScript) and create your game!

# How to...


# Conventions and project structure

- `addons/`
  - This folder contains the base files of Maack's Game Template used in this project.
- `assets/`
  - Contains textures, sprites, sounds, music, fonts, ...
- `audio_setup/`
  - Contains default audio bus layout including three layers: Master, SFX, and BGM
- `builds/`
  - output directory for game builds (ignored by .gitignore and .gdignore)
- `scenes/`
  - Contains Godot scenes (both entities, reusable scenes and "game screen" scenes)
  - Files are grouped into one folder per scene. Reusable scene objects could be grouped differently.
  - Scene folders can contain `.gd` scripts or resources used by the scene

This has been derived from Godot's official [project guidelines](https://docs.godotengine.org/en/stable/getting_started/workflow/project_setup/project_organization.html#style-guide)

### Lower Case file names

This convention avoids having filesystem issues on different platforms. Stick with it
and it will save you time. Read more
[here](https://docs.godotengine.org/en/stable/getting_started/workflow/project_setup/project_organization.html#case-sensitivity):

> Windows and recent macOS versions use case-insensitive filesystems by default,
> whereas Linux distributions use a case-sensitive filesystem by default. This
> can cause issues after exporting a project, since Godot's PCK virtual
> filesystem is case-sensitive. To avoid this, it's recommended to stick to
> snake_case naming for all files in the project (and lowercase characters in
> general).

See also [this PR](https://github.com/godotengine/godot/pull/82957/files) that adds `is_case_sensitive()`.


# Export utilities

Following [Crystal-Bit's Godot Game Template](https://github.com/crystal-bit/godot-game-template), we provide export utilities to automatically create builds for various target systems.

## `release.sh`

From your project root:

```sh
./release.sh MyGameName # this assumes that you have a "godot" binary/alias in your $PATH
```

Look inside the ./builds/ directory:

```sh
builds
└── MyGameName
	├── html5
	│   ├── build.log # an export log + build datetime and git hash
	│   ├── index.html
	│   ├── ...
	├── linux
	│   ├── MyGameName.x86_64
	│   └── build.log
	├── osx
	│   ├── MyGameName.dmg
	│   └── build.log
	└── windows
		├── MyGameName.exe
		└── build.log
```

## Github Actions

If you are using Github you can take advantage of:

1. automatic exports for every commit push (see [push-export.yml][ci-push-export])
2. manual exports via Github CI (see [dispatch-export.yml][ci-dispatch] )

[ci-push-export]: ./.github/workflows/push-export.yml
[ci-dispatch]: ./.github/workflows/push-export.yml

You can read more on [Wiki - Continuos Integration][wiki_ci]

[wiki_ci]: https://github.com/crystal-bit/godot-game-template/wiki/1.-Continuous-integration-(via-GitHub-Actions)


# Thanks

This repository has been derived from:
- [Crystal-Bit's Godot Game Template](https://github.com/crystal-bit/godot-game-template)
- [Maaack's Godot Game Template](https://github.com/Maaack/Godot-Game-Template)

