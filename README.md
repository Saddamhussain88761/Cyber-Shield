# SME CyberShield - Full Project

Complete cybersecurity risk management project aligned with **NIST CSF 2.0** and **ISO 27005**, including backend modules, multi-page Streamlit dashboard, tests, and evaluation artefacts.

## Core Files Included

- `module1_govern_identify.py` - Governance policies, asset inventory, risk scoring, risk register generation.
- `module2_protect_detect.py` - Protective controls, detection mechanisms, coverage metrics, event simulation.
- `module3_respond_recover.py` - Incident playbooks, recovery plans, in-memory incident tracker.
- `module4_integration.py` - Risk aggregation, maturity scoring, heatmap data, full reporting, scenario runner.
- `data_schemas.py` - Shared TypedDict schemas for consistent JSON-style outputs.
- `sample_data.py` - Three complete SME scenarios:
  - `retail_ransomware`
  - `services_phishing`
  - `manufacturing_breach`
- `app.py` + `pages/` - Multi-page Streamlit dashboard UI.
- `utils/` - Reusable charts and export helpers.
- `tests/` - Full pytest suite.
- `evaluation/` - Scenario metrics, heuristics, and NIST benchmark scripts/outputs.
- `docs/` - User guide, technical documentation, final report template.

## Setup

1. Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows PowerShell:

```bash
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

## Run Dashboard

```bash
streamlit run app.py
```

## Quick Backend Usage

```python
from module1_govern_identify import get_asset_inventory, generate_risk_register
from module4_integration import run_sme_scenario

assets = get_asset_inventory()
risk_register = generate_risk_register(assets)

result = run_sme_scenario("retail_ransomware")
print(result["summary"])
print(result["maturity_scores"])
```

## Output Design Notes

- All module outputs are Python dict/list structures and are JSON-serializable.
- `pandas` is used for internal analytics transformations and then converted back to dict/list outputs.
- Data structures are kept consistent with `data_schemas.py` to support direct Streamlit integration in Part 2.

## Testing and Evaluation

Run tests:

```bash
python -m pytest
```

Windows automated run:

```bash
.\run_all_tests.ps1
```

Bash automated run:

```bash
bash run_all_tests.sh
```

## Notes

- All tables support sorting and include relevant page-level filters.
- Export outputs are available from the Integration Dashboard page (PDF + JSON).
