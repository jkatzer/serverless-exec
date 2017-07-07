# Serverless Exec

[![serverless](http://public.serverless.com/badges/v3.svg)](http://www.serverless.com)
[![npm](https://nodei.co/npm/serverless-exec.png?mini=true)](https://www.npmjs.com/package/serverless-exec)

A Serverless v1.x plugin to drop to execute commands with your environment
variables from `serverless.yml`.


## Install

```
npm install --save serverless-exec
```

Add the plugin to your `serverless.yml`:

```yaml
plugins:
  - serverless-exec
```

## Usage
```
$ serverless exec "make test"
Serverless: Executing make test...
YOUR TESTS PASS AND YOU ARE AWESOME
```

### Per function & stage specific env vars
Since the main reason for building this was to test code with the configs for
various stages, it supports properly building the environment. For example:
```
$ serverless -s staging shell -f status
```

### This was forked because
We don't need to sanitize shell inputs in a script utility thats run on
the shell.

Using serverless-shell (a great plugin), in this fashion:
```
$ serverless shell -S $SHELL
```

Executes your shells `.shellrc` or `.shell_profile` which will clobber a
python virtualenv.

And, passing args was not supported `$ serverless shell -S "make test"`
because of the NodeJS sanitzation of inputs... which is probably a
really good idea if you are running NodeJS in production. Personally I
prefer NoJS because I have class. This plugin has class, so it was very
pleasant to modify. This functionality seemed different enough from the
original for a fork. At first I tried:
```
$ serverless shell -x "make test"
```
Which seemed like a hack.

Thanks to the original author(s).
