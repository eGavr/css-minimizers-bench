# css-minimizers-benchmark (CMB)

Сompares the work of **CSS** minimizers.

## What does it already support?

### Minimizers:

* [CSSO](http://bem.info/tools/optimizers/csso/)

* [clean-css](https://github.com/GoalSmashers/clean-css)

* [cssshrink](https://github.com/stoyan/cssshrink)

* [csswring](https://github.com/hail2u/node-csswring)

### Archivers:

* [gzip](http://www.gzip.org/)

## Install

```bash
$ git clone https://github.com/eGavr/css-minimizers-benchmark.git

$ cd css-minimizers-benchmark

$ npm install
```

## Usage

```bash
$ bin/compare-minimizers
```

## Configuration

### How to configure paths?

Go to the [configuration file](https://github.com/eGavr/css-minimizers-benchmark/blob/master/.cmb/config.js#L20). In this file you can configure paths with the help of these variables:

* `toRawCSS` - path to tests (raw, not minimized **CSS** files).
* `toMinCSS` - path where to output minimized **CSS** files.
* `toArchCSS` - path where to output archived **CSS** files.

### How to add your minimizer?

**1**. Go to the [package.json](https://github.com/eGavr/css-minimizers-bench/blob/master/package.json#L27) and add your minimizer to the dependencies.

**2**. Go to the [configuration file](https://github.com/eGavr/css-minimizers-benchmark/blob/master/.cmb/config.js#L9) and add your code according to the following template:

```js
name: minimize(require('module'), 'method')
```

where:

 * `name` - the name of your minimizer (it will be used in the log).
 * `module` - the required module of your minimizer.
 * `method` - the name of the minimization method of your minimizer (the method which recieves a raw **CSS** and minifies it).

**3**. Reinstall the dependencies.

```bash
npm install
```

**4**. See the [usage](https://github.com/eGavr/css-minimizers-bench#usage).

### How to add your archiver?

**1**. Go to the [configuration file](https://github.com/eGavr/css-minimizers-benchmark/blob/master/.cmb/config.js#L16) and add your code according to the following template:

```js
name: archive('bash script', 'suffix')
```

where:
 * `name` - the name of your archiver (it will be used in the log).
 * `bash script` which archives the file. This script provides several **keywords**:
  * `[FILE_PATH]` will be replaced with the paths of all files which were minimized by all specified in the [configuration file](https://github.com/eGavr/css-minimizers-bench/blob/master/.cmb/config.js#L9) minimizers.
  * `[TO_ARCH_CSS]` will be replaced with the path which you have specified in variable `paths.toArchCSS` in the [configuration file](https://github.com/eGavr/css-minimizers-bench/blob/master/.cmb/config.js#L23).
 * `suffix` which is added to a file by the archiver.

**2**. See the [usage](https://github.com/eGavr/css-minimizers-bench#usage).

## License

[MIT License](http://en.wikipedia.org/wiki/MIT_License)
