# Copilot instructions for Astraeus

## Big picture architecture
- Astraeus is a constellation of engines: each engine owns its schema, config namespace, logic, personality, symbolic language, and safety boundaries.
- All engines are connected by shared infrastructure: a universal engine contract, shared context map, shared response builder, shared safety layer, shared mode system, and shared time-safety system.
- Two main roots exist: `backend/` and `frontend/`, suggesting a split API/service layer and UI layer.

## Repo layout (current)
- `backend/src/` contains domain folders: `api/`, `engines/`, `innervoice/`, `micro/`, `orchestrator/`, `persona/`, `response/`, `runtime/`, `safety/`, `signals/`, `state/`, `types/`, `utils/`.
- `frontend/src/` contains UI folders: `components/`, `context/`, `hooks/`, `styles/`, `utils/`.
- `config/` contains engine namespaces and shared configuration roots: `awakening/`, `spiritual/`, `symbolic_identity/`, `metadata/`, `modes/`, `prompts/`, `schema/`.

## Workflows and tooling
- No build/test/run configuration files were found (no `package.json`, `*.csproj`, `*.sln`, or scripts).
- The only config present is `.vscode/settings.json` with editor/Chat preferences; it does not define build or debug tasks.

## Conventions & patterns (discoverable)
- Place backend code under `backend/src/<domain>/` and frontend code under `frontend/src/<ui-area>/` to match the existing layout.
- Keep new modules aligned with the existing folder names; they describe intended boundaries (e.g., `orchestrator`, `signals`, `state`).
- Engine contract inputs: `user_context`, `worldview_map`, `mode_state`, `time_safety_state`, `engine_config`, `depth_preference`, `intrigue_state`.
- Engine contract outputs: `reflection_prompt`, `symbolic_lens` (optional), `grounding_note` (optional), `suggested_mode_shift` (optional), `safety_flag` (optional), `intrigue_pulse_request` (optional), `self_voice_reflection` (optional), `engine_trace` (optional).
- Shared context map keys (write/read consistently): `worldview_map.spiritual_background`, `symbolic_identity`, `zodiac_profile`, `planetary_profile`, `awakening_state`, `mythic_resonance`, `emotional_mode`, `depth_preference`, `avoidance_patterns`.
- Response building should always pass through tone blending, safety filtering, pacing adjustment, mode alignment, and clarity shaping.
- If `self_voice_reflection` is true, apply the Inner Voice filter and tone profile (first-person, soft, non-judgmental) when the current mode allows it.
- Intrigue pulse is adaptive/mysterious/soft: trigger only when time-safety and mode checks pass, and use user-voice phrasing for growth moments.
- Engine schemas should follow the universal pattern: `engine_name.schema.yaml` with required `prompts`, `patterns`, `reflection_paths` and optional `archetypes`, `symbolic_mappings`, `grounding_sequences`, `escalation_rules`.
- Master engine schema lives at `/config/schema/engine.master.schema.yaml` and includes id/name/description, prompts, patterns, reflection paths, lenses, depth profile, tone profile, cross-engine hooks, intrigue pulse, and safety profile.
- Universal engine design philosophy: engines are self-contained, symbolically coherent, safe (no diagnosis/prediction/directive), reflective (return the user to themselves), interoperable (shared contract/context), mode-aware (tone/pacing adapts), and time-safe (respect session boundaries and emotional pacing).

## Integrations
- No external integrations, service endpoints, or dependencies are declared yet.

## TODO for maintainers
- Add build/test instructions and any architecture notes to `docs/` or a root `README.md` so agents can follow real workflows.
