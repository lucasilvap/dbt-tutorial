# Jaffle Shop dbt Project

Welcome to the Jaffle Shop dbt project! This project provides a sample dbt setup for a fictional e-commerce store called Jaffle Shop. It demonstrates how to use dbt to transform raw data into clean, well-defined, and tested data models.

## Project Overview

This dbt project takes raw customer and order data and transforms it into a structured format that is ready for analysis. The project includes:

- **Staging models**: To clean and standardize the raw data.
- **Final models**: To join the staging models and create a final, unified view of the data.
- **Tests**: To ensure data quality and integrity.

## Project Structure

This project follows the standard dbt project structure:

- `models/`: Contains the SQL definitions for all the data models.
  - `staging/`: Contains models that clean and prepare the raw data.
  - `marts/`: Contains the final models that are exposed to end-users. (Note: this project uses a flat structure for simplicity, but a `marts` directory is a common convention).
- `macros/`: Contains any custom macros used in the project.
- `seeds/`: Contains any seed data for the project.
- `tests/`: Contains any custom tests for the project.
- `dbt_project.yml`: The main configuration file for the dbt project.
- `profiles.yml`: The configuration file for connecting to your data warehouse. (You will need to create this file).

## Setup

To get this project up and running, you will need to do the following:

1.  **Install dbt and the necessary adapter.** This project uses BigQuery, so you will need to install `dbt-core` and `dbt-bigquery`.

    ```bash
    pip install dbt-core dbt-bigquery
    ```

2.  **Set up your `profiles.yml` file.** This file contains the connection details for your data warehouse. You will need to create a `profiles.yml` file in your home directory (`~/.dbt/`) or in the root of this project. Here is an example configuration for BigQuery:

    ```yaml
    jaffle_shop:
      target: dev
      outputs:
        dev:
          type: bigquery
          method: service-account
          project: <your-gcp-project-id>
          dataset: <your-bigquery-dataset>
          threads: 1
          keyfile: <path-to-your-service-account-json>
    ```

    For more information on setting up your profile, see the [dbt documentation](https://docs.getdbt.com/dbt-cli/configure-your-profile).

3.  **Install the project dependencies.** This project does not have any external dbt package dependencies, but if it did, you would run the following command:

    ```bash
    dbt deps
    ```

## Usage

Once you have completed the setup, you can run the dbt models and tests.

- **Run the models:**

  ```bash
  dbt run
  ```

  This command will execute all the models in the `models/` directory.

- **Run the tests:**

  ```bash
  dbt test
  ```

  This command will run all the tests defined in the `schema.yml` files.

This project is a great starting point for learning dbt. For more information, please see the official [dbt documentation](https://docs.getdbt.com/docs/introduction).
