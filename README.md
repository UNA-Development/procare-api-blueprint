Procare API Blueprint
=====================

This is an API Blueprint for the proposed Procare API. It follows a format easily parsed as either HTML documentation or executable test suite for an API.

* Read the [API Blueprint Documentation](http://apiary.io/blueprint) for more information on the syntax.


## Getting Started

This requires [node](http://nodejs.org/) and [npm](https://npmjs.org/‎).

1. Install dependencies:

   ``` bash
   $ npm install -g grunt-cli
   $ npm install
   ```

2. Run the preview server:

   ``` bash
   $ grunt docs -a
   ```

The blueprint is built from the files in `/parts`, and are concatenated in file-system order. Do **not** commit the compiled `blueprint.md` file (it will be ignored/overwritten).

# Workflows

## Implement new API

1. Document new API in Blueprint

   ``` bash
   $ grunt docs -i parts/08-Appointments.md
   ```

   Edit `parts/08-Appointments.md`, changes will be visible at `http://localhost:3002/` (refresh to see changes)

2. (optional) Run generated tests against generated mock server

   ``` bash
   $ grunt mock -i parts/08-Appointments.md
   $ grunt test -i parts/08-Appointments.md
   ```
   This will help identify small mistakes, like invalid json or improper blueprint formatting.

3. Implement API in project

4. Run tests against API

   ``` bash
   $ grunt test -i parts/08-Appointments.md -e http://localhost:5000/
   ```

5. Check that full document merges properly

   ``` bash
   $ grunt docs -a
   ```

6. Commit and push changes

## Develop a client against documented API

1. Run mock server

   ``` bash
   $ grunt mock -a
   ```

2. Point client to mock server. By default, the mock server runs on port 3001.

# Tasks

## Generate Docs

By default (no flags), the document generated uses the contents of `./blueprint.md`.

### View Generated Docs

   ``` bash
   $ grunt docs -a
   ```

### View Single File Generated Docs

   ``` bash
   $ grunt docs -i ./parts/07-Offices.md
   ```

### Options

 * `-t` - Specify custom Jade template for styling generated html.
 * `-i` - Specify input file/input files to view.
 * `-a` - Merge all `.md` documents in `/parts` and save in `./blueprint.md`, then start the blueprint server.



## Run Mock Server

By default, the mock server starts up with the contents of `./blueprint.md`.

### Run Full Mock Server

   ``` bash
   $ grunt mock -a
   ```

### Run Single File Mock Server

   ``` bash
   $ grunt mock -i ./parts/07-Offices.md
   ```

### Options

 * `-p` - Specify port for mock server to run on.
 * `-i` - Specify input file/input files to mock.
 * `-a` - Merge all `.md` documents in `/parts` and save in `./blueprint.md`, then start the mock server.

## Run Tests

By default, the test command points to `http://localhost:3001`.

### Run All Tests Against a Live Server

   ``` bash
   $ grunt test -a -e https://api.procarerx.com/
   ```

### Run Subset of Tests Against a Live Server

   ``` bash
   $ grunt test -i ./parts/07-Offices.md -e https://api.procarerx.com/
   ```

### Options

 * `-e` - Specify the root api endpoint to test against.
 * `-i` - Specify input file/input files to test.
 * `-a` - Merge all `.md` documents in `/parts` and save in `./blueprint.md`, then start the tests.

## Merge Parts

This command merges everything that matches `/parts/*.md` and saves it in `./blueprint.md`. Note that this implies filesystem ordering for concatenation.

   ``` bash
   $ grunt merge
   ```
## Finer Control
If you need finer control of any of these steps, use the tools listed in the `package.json` manually.
