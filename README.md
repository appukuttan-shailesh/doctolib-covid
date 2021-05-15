## Update (Shailesh Appukuttan)

Email notifications were found to be too slow to be effective (as the slots were found to be booked very quickly)
So the script has been updated to do the following:

1. checks multiple centers in parallel, thereby speeding up search
   - set number of cores
2. sounds an alarm for each available center with slots
3. auto opens the doctolib page for the center when slots are found

### Usage:

- Set the vaccination centers close to your location in [centers.txt](../master/centers.txt)

- Execute command
  `$ python doctolib-covid_multiprocess.py`

(unchanged docs from source repo below)

## Doctolib COVID

This script sends email alerts (using Google SMTP server) when vaccination appointments are available on Doctolib.

## Prerequisites

- Python 3

## Download dependencies

`$ pip install -r requirements.txt`

## Execution

- Set the vaccination centers close to your location in [centers.txt](../master/centers.txt)

- Set environment variables

  - DISABLE_EMAIL: set to true to disable email alerts
  - SENDER_EMAIL: the sender email address
  - SENDER_PASSWORD: the associated password
  - RECEIVER_EMAIL : the receiver email address

- Execute command
  `$ python doctolib-covid.py`

- Output example

```
0 appointments available at Centre de Vaccination - Salle Olympe de Gouges - 15 Rue Merlin, 75011 Paris
0 appointments available at Centre de Vaccination - Centre Bertheau - 15-17 Rue Charles Bertheau, 75013 Paris
0 appointments available at Centre de Vaccination - Mairie Paris Centre - 2 Rue Eugène Spuller, 75003 Paris
5 appointments available at Centre de Vaccination - Mairie du 13e - 1 Place d'Italie, 75013 Paris
  --> Alert sent to me@bntan.com
0 appointments available at Centre de Vaccination - Le 104 - 5 Rue Curial, 75019 Paris
0 appointments available at Centre de Vaccination - Paris 20e - 87 Rue des Haies, 75020 Paris
0 appointments available at Centre de vaccination Aubrac - 10 Rue de l'Aubrac, 75012 Paris
0 appointments available at Centre de Vaccination - Mairie du 10e - 72 Rue du Faubourg Saint-Martin, 75010 Paris
[...]
```

## Cron

Use [cron-doctolib-covid.yml](../master/.github/workflows/cron-doctolib-covid.yml) to schedule the script execution. Uncomment the `schedule` section.
The example below executes the script every 5 minutes

```yaml
name: Cron Doctolib COVID

on:
  [...]
  schedule:
    - cron: "*/5 * * * *"

[...]
```
