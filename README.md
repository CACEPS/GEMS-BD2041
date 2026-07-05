# GEMS-BD2041
A dynamic CGE assessment of Bangladesh’s Vision 2041
# DyCGE Bangladesh Vision 2041: Replication Package

Replication materials for: *Auditing long run development targets in
emerging economies: A dynamic CGE assessment of Bangladesh's Vision
2041*.


## Contents

- `model/DyCGE_Vision2041_AllInOne.gms`  THE single complete
  replication file: readme, balanced FY2019 SAM (built in),
  data completion rules, elasticities, calibration, the full
  within period model, the recursive dynamic loop with the S5.1
  partially endogenous TFP linkage, all scenarios, and reporting.
  Nothing else is required to reproduce the paper's simulations.
- `model/legacy/`  Earlier split files (DyCGE_BD2041.gms,
  tfp_linkage.gms), superseded by the all in one file and kept
  only for documentation of the revision history.
- `scripts/run_all.sh`, `scripts/run_all.bat`  Full replication
  batch: 19 runs covering the three core scenarios, the five
  single lever runs (Table 6), the partial reform scenario, the
  elasticity sets (Table A12), the fertility variants (Section
  5.4), and the TFP linkage sweep (Table A8). Collects one line
  per run in `DyCGE_summary.csv`.
- `scripts/mc_surrogate.py`  Surrogate Monte Carlo (main text
  Table 8, Figure 8). Seed 2041. Update its anchor constants from
  the SCEN=1 and SCEN=9 lines of `DyCGE_summary.csv` after the
  batch completes.
- `data/`  The SAM is embedded in the .gms file (SECTION 2) with
  provenance and estimation rules E1 to E9 documented in the file
  header. `README_data.md` describes the account structure.
- `scenarios/`  Driver paths are generated inside the .gms file
  (SECTION 7), matching Supplementary Tables A9 to A11.
  `README_scenarios.md` maps scenario codes to the paper.
- `results/`  Place `DyCGE_summary.csv` and per run
  `DyCGE_results.csv` exports here after running the batch.

## Scenario codes (--SCEN=)

1 BAU | 2 Vision 2041 target | 3 Downside | 4 SL1 FDI | 5 SL2 TFP |
6 SL3 population | 7 SL4 direct tax | 8 SL5 interest spread |
9 Partial reform

Switches: `--ELAST=1|2|3` (low/central/high elasticities),
`--FERT=1|2|3` (UN fertility variants), `--TFPSCALE=0.5|1.0|1.5`
(S5.2 coefficient sweep). All compose with any scenario.

## How to run

1. Install GAMS 25.0.x with CONOPT (or delete `NLP=CONOPT` in the
   OPTION line to use the default NLP solver).
2. Single run: `gams model/DyCGE_Vision2041_AllInOne.gms --SCEN=1`
3. Full batch: from `model/`, run `../scripts/run_all.sh`
   (Linux/macOS) or `..\scripts\run_all.bat` (Windows).
4. Outputs: `DyCGE_results.csv` (annual trajectories, last run) and
   `DyCGE_summary.csv` (one line per run: SCEN, ELAST, FERT,
   TFPSCALE, 2041 per capita income, UMIC and HIC crossing years).

## Mapping to the paper

- Table 2, 3: SCEN=1 trajectories (`DyCGE_results.csv`).
- Tables 4, 5: sectoral value added and employment from SCEN=1 and 2.
- Table 6, Figure 6: SCEN=4 to 8 versus SCEN=1 summary lines.
- Table 7: SCEN=1, 2, 3 summaries.
- Table 8, Figure 8: `scripts/mc_surrogate.py` with updated anchors.
- Table A12: ELAST=1/3 runs. Table A8: TFPSCALE=0.5/1.5 runs.
- Figures 2, 3, 9: PCUSD paths across scenarios.

## Citation and licence

Please cite the paper and this archive (Zenodo DOI to be minted on
acceptance). Code released under the MIT licence; data under CC BY 4.0.

## Contact

Questions during review: via the journal's editorial system.

