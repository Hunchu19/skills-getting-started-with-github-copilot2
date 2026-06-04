## Plan: Add backend FastAPI tests

TL;DR - Add a new `tests/` directory with pytest-based API tests for `src/app.py`, including signup and unregister coverage.

**Steps**
1. Create `tests/test_app.py`.
   - Import `TestClient` from `fastapi.testclient`.
   - Import `app` from `src.app`.
   - Use a fresh `TestClient(app)` in test functions.
2. Implement tests using the AAA pattern (Arrange, Act, Assert):
   - `test_get_activities_returns_activities`
   - `test_signup_for_activity_adds_participant`
   - `test_signup_duplicate_returns_400`
   - `test_unregister_participant_removes_participant`
   - `test_activity_not_found_returns_404`
3. Ensure the repository can resolve `src.app` by using the existing `pytest.ini` pythonpath setting.
4. Add `requests` to `requirements.txt` if required for `TestClient` to work in a clean environment.

**Relevant files**
- `/workspaces/skills-getting-started-with-github-copilot2/tests/test_app.py` - new test file
- `/workspaces/skills-getting-started-with-github-copilot2/requirements.txt` - may need `requests`
- `/workspaces/skills-getting-started-with-github-copilot2/pytest.ini` - already configures `pythonpath = .`

**Verification**
1. Run `pytest tests/test_app.py`.
2. Confirm all routes behave as expected:
   - GET `/activities` returns a dictionary with activity entries
   - POST signup works and then GET reflects the added participant
   - duplicate signup returns status 400
   - DELETE participant removes the participant from the activity
3. If using `TestClient`, ensure `requests` is installed or added to `requirements.txt`.

**Decisions**
- Use pytest and FastAPI's `TestClient` because it is straightforward and fits the existing backend.
- Keep tests separate from `src/` in a top-level `tests/` folder.
