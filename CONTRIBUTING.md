# Contributing to AgriGuard

AgriGuard is a hackathon prototype for crop-disease diagnosis. Contributions
that improve model quality, accessibility, documentation, or the reliability of
the upload flow are welcome.

## Development setup

1. Fork the repository and clone your fork.
2. Create a virtual environment and install the backend dependencies:

   ```bash
   python -m venv .venv
   # Windows PowerShell
   .venv\Scripts\Activate.ps1
   # macOS / Linux
   source .venv/bin/activate

   pip install -r backend/requirements.txt
   ```

3. Provide a compatible model at
   `backend/model/model_output/crop_disease_model.h5`, or train one from
   PlantVillage as described in the README. The `.h5` file and raw dataset are
   intentionally ignored by Git.
4. Start the API from the repository root:

   ```bash
   python backend/main.py
   ```

5. In a second terminal, serve the frontend:

   ```bash
   cd frontend
   python -m http.server 3000
   ```

For local UI work, point `API_URL` in `frontend/js/script.js` at
`http://localhost:8000/predict`. Do not commit a machine-specific API URL unless
it is intentionally the project default.

## Branch naming

- `feat/<short-description>` — new user-facing capability
- `fix/<short-description>` — bug fix
- `docs/<short-description>` — documentation
- `model/<short-description>` — training or inference changes
- `chore/<short-description>` — maintenance

Keep branches focused. Do not mix model changes, UI redesigns, and dependency
updates in one pull request.

## Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```text
feat(api): return a structured error for unsupported images
fix(frontend): reject files larger than 10 MB
docs(model): explain the class ordering requirement
```

Write the subject in the imperative mood and keep it under about 72 characters.
Use the body to explain the reason for the change and any behavior that is not
obvious from the diff.

## Code guidelines

- Keep the class order in `class_names.json` aligned with the output layer of
  the model. A mismatch silently produces wrong labels.
- Treat the model as a screening tool. Do not present predictions as confirmed
  diagnoses or add language that promises clinical or agronomic accuracy.
- Validate uploads on the server, not only in the browser.
- Do not commit datasets, model weights, generated images, or credentials.
- Keep the frontend dependency-free unless a new dependency is clearly
  justified. It is intentionally plain HTML, CSS, and JavaScript.
- Preserve the existing visual identity and responsive behavior when changing
  the UI.
- Use `textContent` for values derived from model output or user input.

## Checks before opening a pull request

There is no automated test suite or linter configuration yet. Run at minimum:

```bash
python -m compileall backend
```

Then start the backend and verify:

```bash
curl.exe http://localhost:8000/
curl.exe -X POST http://localhost:8000/predict \
  -F "file=@frontend/assets/images/rice_blast_1.jpg"
```

Manual UI checks:

- Upload a valid leaf image and confirm the result page renders the class and confidence.
- Try an unsupported file type and a file over 10 MB; both should be rejected client-side.
- Confirm the regional disease page still loads for each supported state.
- Check the layout at a narrow mobile width.

If you changed the model, document the dataset, class set, training command, and
observed evaluation metrics. Do not report accuracy without a reproducible
evaluation split.

## Pull request checklist

- [ ] The change is scoped to one problem and described clearly.
- [ ] `python -m compileall backend` passes.
- [ ] The upload and prediction flow was tested end to end.
- [ ] Any model change includes dataset, class order, and evaluation details.
- [ ] No `.h5`, dataset images, secrets, or generated files are included.
- [ ] Documentation was updated for user-visible changes.
- [ ] The PR follows the [Code of Conduct](CODE_OF_CONDUCT.md).

## Reporting issues

Use the templates in `.github/ISSUE_TEMPLATE/`. Include the browser, operating
system, Python version, whether a model checkpoint was present, and the backend
traceback. Redact any personal or sensitive data from images and logs.

Report security vulnerabilities privately per [SECURITY.md](SECURITY.md).
