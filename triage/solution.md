# PASS

Your solution to TRIAGE passed!

Here's what the official solution is if you want to compare notes:

    var fs = require("fs");

    var peach = function (obj) {
      console.trace("traced");
      console.log(obj);
    };

    var bowser = function (callback) {
      fs.readFile(process.argv[2], {encoding : "utf8"}, callback);
    };

    var koopa = function (err, file) {
      if (err) return console.error("Handle your errors folks.");

      peach(JSON.parse(file));
    };

    bowser(koopa);

You have 11 challenges left.
Type `bug-clinic` to show the menu.
