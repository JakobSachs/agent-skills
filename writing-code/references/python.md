# Python

## Tooling

- `uv` for everything: dependencies in `pyproject.toml` (or a script shebang with inline metadata), `uv run` for tools, `uv venv` for environments.
- After a dependency change: `uv lock`, commit `uv.lock`.
- Format with black and isort (or the repo's ruff config). Type-check with mypy, lint with pylint or ruff, test with pytest: whichever the repo uses, via `uv run`.

## Style

- Type hints on every function and class. Annotate variables where the type is not obvious.
- Use the standard library before adding a dependency or writing your own (`itertools`, `functools`, `collections`, `dataclasses`, `pathlib`, `contextlib`).
- Comprehensions (list, dict, set, generator) over loops that build collections.
- The walrus operator to assign where the value is used: `if (m := pattern.match(s)):`, inside comprehensions, in `while` loops.
- Dense but readable: fewer lines is good until it costs clarity.

## Types in Python

- `@dataclass(frozen=True, slots=True)` for core types; pydantic at boundaries (JSON, env, forms) unless the project uses it throughout.
- Sum types: a union of frozen dataclasses with exhaustive `match` and `assert_never` in the default arm.
- `typing.NewType` for zero-cost IDs; a small frozen dataclass with a `parse` classmethod when there is validation.
- `Literal[...]` or `Enum` for fixed vocabularies. No `Any` in core types.

## Tests

pytest with hypothesis. Shared strategies in a `strategies.py` or `conftest.py` per domain.
