# awesome-android-claude-skills

A curated collection of [Claude Code](https://claude.ai/claude-code) skills for Android development.
Built for modern Android apps with Kotlin, Jetpack Compose, and Clean Architecture.

## Skills

| Skill | Description | Language |
|-------|-------------|----------|
| [recommend-commit-message](./skills/recommend-commit-message/) | Analyze staged changes and recommend Conventional Commits messages with Android layer hints | Multi (ENG default) |

## Target Stack

Skills are designed for projects using:

**Kotlin** · **Jetpack Compose** · **Clean Architecture** · **Hilt** · **Coroutines + Flow** · **Retrofit** · **Gradle Version Catalogs**

## Installation

```bash
# 1. Clone this repo
git clone https://github.com/your-username/awesome-android-claude-skills.git

# 2. Copy a skill into your project
cp -r awesome-android-claude-skills/skills/recommend-commit-message /your-project/.claude/skills/
```

Then invoke it in Claude Code:

```
/recommend-commit-message
```

## Contributing

Contributions are welcome! To add a new skill:

1. Create a folder under `skills/your-skill-name/`
2. Add `SKILL.md` (skill instructions) and `README.md` (usage guide)
3. Update the Skills table in this README
4. Open a PR

## License

MIT
