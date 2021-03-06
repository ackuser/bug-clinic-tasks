#####################################################################
##                         ~~  TRIAGE  ~~                          ##
#####################################################################

If you can run your program interactively, and your program has access
to a console, then it's pretty likely that you're going to spend much
of your debugging time adding print statements to your program and
modules. Unless you're diagnosing an issue in a running production
service, printing is the fastest and simplest way to start figuring
out what's wrong with your program.

Node includes some basic functions for output, not all of which are
well-known:

console.log(arguments): print to standard output
console.error(arguments): print to standard error

Two things to know about these functions:

1. You can pass as many comma-separated parameters to them as you
 like, and the results will be printed separated by spaces.
2. The parameters to the call are passed to Node's util.format(),
 so you can use %s (for strings), %d (for numbers), and %j (for
 objects, passed through JSON.stringify()), just as you would
 in a call to util.format().

For debugging, there are a few more useful methods:

console.trace(label): dump stacktrace at line trace is called, with label
console.time(label) / console.timeEnd(label): quick & dirty benchmarking
console.assert(expression, arguments): assert that expression is true
console.dir(object): call util.inspect() on `object`, print results

In day-to-day debugging, console.error, console.dir and console.trace
are the most useful of these functions. They will give you the why,
the what, and the where without requiring a bunch of extra effort.

## CHALLENGE

Here's a simple exercise to get you comfortable with using the console
methods. Replace the comments in the following program (which you can
save as scenario.js) with the relevant calls to the console API:

  // scenario.js
  var fs = require("fs");

  var peach = function (obj) {
    // trace the message "traced"
    // dump obj to stdout
  };

  var bowser = function (callback) {
    fs.readFile(process.argv[2], {encoding : "utf8"}, callback);
  };

  var koopa = function (error, file) {
    // handle error by printing something to stderr

    peach(JSON.parse(file));
  };

  bowser(koopa);

If you want some sample JSON to play with, store the following in
`test-input.json` and then parse it by running `node scenario.js
test-input.json`.

  {
      "mushroomKingdom": [
          "Super Mario Bros",
          "Super Mario Bros 2",
          "Super Mario Bros 3",
          "Super Mario World",
          "Super Mario 64",
          "Super Mario Sunshine",
          "Super Mario Galaxy"
      ]
  }


To verify your program, run: `bug-clinic verify program.js`.
