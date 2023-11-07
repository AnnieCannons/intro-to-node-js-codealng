# Intro to Node.js Codealong

This codealong will get you some hands-on experience with Node.js.

### The Instructor's "I Do" Portion

This part should be done by the instructor alone, with the understanding that the students will ask questions but not worry about doing this themselves. The student role for this part is simply to see how Node executes files.

#### Setup

The instructor should already have made a file, have it open in VS Code, and be ready to run it using Node in the terminal. The "We Do" portion will show them how they can create their own files and manage VS Code and/or the terminal themselves.

#### The Final "I Do" Code

Here is the solution for immediate reference.

```javascript
let date = new Date();
let fullDate = date.toDateString();
let day = fullDate.slice(0, 3);

console.log("Today's date is " + fullDate + ".\n");

if (day === "Mon") {
  console.log("Happy Monday! Hope you have a great work week.");
} else if (day === "Tue") {
  console.log("Happy Tuesday! Hope it's even better than your Monday was.");
} else if (day === "Wed") {
  console.log("Happy Hump Day!");
} else if (day === "Thu") {
  console.log("It's almost Friday, whoooooo!");
} else if (day === "Fri") {
  console.log("TGIF!!");
} else if (day === "Sat") {
  console.log("Welcome to the weekend!");
} else if (day === "Sun") {
  console.log("Don't get the Sunday scaries...");
} else {
  console.log(
    "Something has gone very wrong in our code or in our calendar..."
  );
}
```

#### Suggestions For The Instructor

- Make a simple file first, possibly with just a console.log statement, to show them how you run files with Node. And possibly a different, separate file with similar content, to drive home to students that you have to explicitly tell Node what file to run. Giving them arbitrary files to run can be helpful in dispelling any sense of "magic".
- When you're ready to build the main program above with them, start with a simple version. Could simply be lines 1 and 2 and 5 (the `console.log`).
- If you choose to code this in front of them, consider writing only the if/else statements for today, tomorrow, and Saturday. You can always copy-and-paste in the rest of it after.
- What are our takeaways?
  1. Node can run JS in the same way as the browser, but without an intermediate HTML file.
  2. We run files with Node by entering `node [filename]` on the command line, replacing the word "filename" and its brackets with the path to the file.
  3. Any console.logs in Node-executed code will print out in the terminal.

### Student Codealong ("We Do")

This part will involve the students coding along with the instructor.

#### Solutions

Here are both solutions for immediate reference.

##### Hardcoded Version

This version always gets the same answer, because the inputs are always the same: 4 guests tipping 20% on a $100 restaurant bill

```javascript
let bill = 100;
let tipPercentage = 0.20;
let numGuests = 4;
let tipAmount = bill * tipPercentage;
let total = bill + tipAmount;
let amountOwedPerGuest = total / numGuests;

console.log("Each guest owes: $" + amountOwedPerGuest);
```

##### Dynamic Version

Run this code with `node [filename] [number of guests] [tip percentage] [bill amount]`. For example, you could run `node [filename] 2 25 150` to calculate the bill per guest for 2 guests tipping 25% on a $150 restaurant bill.

```javascript
let bill = process.argv[4];
let tipPercentage = process.argv[3];
let numGuests = process.argv[2];

let tipAmount = bill * tipPercentage;
let total = bill + tipAmount;
let amountOwedPerGuest = total / numGuests;

console.log("Each guest owes: $" + amountOwedPerGuest);
```

#### Setup

First, each student should make sure they have Node.js installed.

Install it through your terminal using the Homebrew package manager's `brew` command, typing `brew install node` and hitting enter on the command line.

If you don't have Homebrew, follow the instructions from Step 1 in [our Git Setup Guide](https://github.com/anniecannons/intro-to-programming-curriculum/blob/main/git/resources/git-and-github-setup-guide.md), which includes steps for installing Homebrew.

##### OPTIONAL: Intermediate Level VS Code Setup

One of the most common ways experienced developers run VS Code is to use the `code` command in their terminals. The typical workflow is:

1. Navigate in the terminal until you're in the directory of the project you want to work with. For example, after running `git clone [repo url]` to download a repo, `cd [repo name]` to get into the directory itself.
2. Run `code .`, with `.` being the terminal shortcut for "the current directory". This opens the current directory in a new VS Code window.

However, this only works if you have the `code` command available in your terminal. If you try to run this and the terminal says `command not found: code`, then you do not have the command available. There are two ways to fix this:

**IF YOU INSTALLED VS CODE FROM VS CODE'S WEBSITE OR THE APP STORE**

1. Make sure that VS Code is in your Applications folder (drag it from Downloads to Applications if it's still in Downloads) and _the file is named_ "Visual Studio Code". If you have more than one copy in your Applications folder, delete any not explicitly called "Visual Studio Code".
2. Enter the following command in your terminal. Do _not_ paste this in 1 line at a time—paste all 4 lines together, then hit enter.

```shell
cat << EOF >> ~/.zprofile
# Add Visual Studio Code (code)
export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
EOF
```

3. Re-open your terminal and the `code` command should work.

**REINSTALL VS CODE THROUGH HOMEBREW**

If you can't get the above to work, or simply want to have everything installed through Homebrew, here's how you can install VS Code through Homebrew, which automatically provides the `code` command.

1. Make sure that VS Code is **NOT** in your Applications folder **OR** your Downloads folder. Drag any copies from anywhere on your system to the Trash, even those under similar names. Then empty the trash.
2. Run the command `brew install --cask visual-studio-code` in your terminal.
3. You may have to open a new terminal to access the `code` command.

#### OPTIONAL: Exploring The REPL Briefly

This can be cut for time, or introduced another time down the road.

You can run the Node REPL by simply typing `node` and hitting enter in any terminal. (If this doesn't work, you don't have Node installed. See previous section.)

Note that you are _not_ in the regular terminal anymore. You are in the Node REPL now, so any `cd` or `git` or any non-JS commands will no longer work. (How to quit back to your regular terminal momentarily.)

Here, you can try evaluating JavaScript and see its results. For example, you can type in:

`let greeting = 'hello';`

Followed by the return key.

This will evaluate to the value of `greeting`, `'hello'`.

Next, you can try this, followed by the returned key:

`greeting.toUpperCase()`

(Don't forget the upper-case letters for U and C there, or the parentheses at the end.)

This will evaluate to `'HELLO'`.

Next you can evaluate `greeting` to see that the variable hasn't changed its value... it's still `'hello'`.

If you don't understand why `greeting.toUpperCase()` didn't change the value of `greeting`, you're in good company, and this is an excellent opportunity to research and ask questions to figure out why. And this is exactly why an easy-to-access REPL is important: you can experiment with code in a low-stakes environment, so that you can learn, and try things, and iterate on your code until you have what you want to put in your final program.

##### Exiting The REPL

You can exit the REPL and go back to your regular terminal prompt with Ctrl-d. Hitting Ctrl-c twice will also work, as will typing `.exit` and hitting return.

#### Running Your First Node.Js Program

##### Creating A File

Create a new file and open it in VS Code. Let's call it `bill-splitter.js`.

If you aren't sure how to do that, here are two methods:

**THE EASY WAY: THE CODE COMMAND**

You can do this any way you like, but if you have the `code` command set up, you can simply enter `code bill-splitter.js` on the command line to both create the file and open it, though you _will_ have to manually save it in Visual Studio Code to finish creating the file.

The nice thing about this is that it's just one step, _and_ you'll still have your original big terminal window open to the right directory and ready to run the file using `node`.

**THE MORE MANUAL WAY**

Alternately, you can:

1. Use `touch bill-splitter.js` in the terminal.
2. Go to VS Code and choose "Open File", which is in the file menu and also available via Command-o.
3. Navigate to the file you created in the terminal in step 1.

##### Our First Console Log Statement

Write the following in your new file:

```javascript
console.log("Hello, this is my first Node program!");
```

Feel free to write whatever message you want!

##### Running It In The Terminal

Either switch back to your main terminal window or switch to the integrated terminal in VS Code. You may have to navigate to the correct directory in the integrated terminal, depending on how you launched VS Code. (Hint: you can let VSC default ot the right directory where you're working by opening the folder instead of a file, either manually through VS Code or with the `code .` command in the terminal, which,if you have the `code` command installed, will open the terminal's current directory in VS Code.)

Once you're in the terminal and in the right place, run `node bill-splitter.js` (or whatever you named the file). You should see your message printed directly to the terminal.

##### Make Some Changes

We can make any changes we want to the file and save it (or have auto-save on), and the next time we run `node [filename]`, the program will run with the new code.

Let's try making a variable:

```javascript
let greeting = "Welcome to Bill Splitter!";

console.log(greeting);
```

##### There's No "Memory"

Every time we run the file, Node is executing the code without any memory of previous times. This is actually great, because it would be an enormous source of bugs if past versions of the file affected future versions.

Try changing the first line to:

```javascript
greeting = greeting.toUpperCase();
```

The declaration of `greeting` from the previous time we ran the file is entirely forgotten, and so we have an error now.

##### Splitting The Bill

Erase any code you have, and let's start writing a program to calculate splitting a restaurant bill

For our first pass at the program, we'll focus on calculating the answer with hardcoded values and outputting it to the terminal. Later, we'll take in actual user input

**ABOUT HARDCODING VALUES**

For now, we'll hardcode the amounts. That means this bill splitter will _not_ be dynamic—each time we run it, we'll get the same amount, and the only way to change the result is to manually re-enter the values in the code.

This does _not_ scale—imagine if you have a notes app on the web, and every time someone takes a note, a JavaScript developer has to manually go in and add a new variable for that note.

And imagine they have to do this with each user!

Instead, _one_ JS developer can write code _one_ time to handle _all_ inputs from the user.

We'll soon enough write our code so that it can handle any input from the user. But for now: hardcoding it.

**HARDCODED VERSION**

Let's say that we have the following variables:

```javascript
// The bill is $100.
let bill = 100;
// We'll tip 20%.
let tipPercentage = 0.20;
// There are four guests.
let numGuests = 4;
```

Now we need to calculate:

1. The total after we add the tip.
2. The total for each guest.

And then we can print out the results with `console.log`

Think about it and try to solve this one your own. (And if you're doing this in class, work on the problem together.)

A common mistake here is to arrive at a total bill of the `tipPercentage` times the `bill`… but that's only the tip, not the total bill!

Here's one version of the rest of the code:

```javascript
let tipAmount = bill * tipPercentage;
let total = bill + tipAmount;
let amountOwedPerGuest = total / numGuests;

console.log("Each guest owes: $" + amountOwedPerGuest);
```

**TAKING INPUT FROM THE USER**

_Environments_

When you're running JS using Node, you have access to some of the same built-in methods, like `console.log`, but for the most part, the "environment" is different, just as you have different environment with different tools available when using Android and iOS devices. (Even `console.log` is slightly different here.)

A good example of this is `alert`, which creates a pop-up box with an "okay" button in a browser environment. While you can print in both places with `console.log`, there are no pop-ups in terminals, and so you'll get an error if you try to use `alert`. That function doesn't exist here unless you yourself make it.

_process.argv_

The same is true of the `prompt` function, but Node _does_ have something similar in the `process.argv` array.

Try adding this to the top of the file:

```javascript
console.log(process.argv);
```

Then run `node [filename]` in your terminal, and you'll see an array print of two strings print to the screen. They are string representations of the two things you typed in the terminal: the absolute path to Node, and the absolute path to the filename.

Now, every word you write _after_ `node [filename]` will get added to that array.

Without changing your code, enter this into the terminal: `node [filename] node is pretty cool` into your terminal and hit enter.

Now you'll see the array have the string representations of the paths to Node and your file as indexes `0` and `1`, but indexes `2`, `3`, `4`, and `5` will each hold one word of what you wrote after the filename.

What we want is to our program so that we can write `node [filename] 2 25 150` and have the bill-splitter app calculate the amount owed for 2 people paying a 25% tip on a $150 restaurant bill.

With our `console.log` of `process.argv` still in our code, try running your file in your terminal with a number of guests, a tip amount, and a total bill, and see how the array prints out.

Pay attention to what index each thing shows up at!

_Putting That Together_

Think for a minute about how to get those values out of the `process.argv` array. Remember, it's just an array, so we can access specific values from it. Try logging different values as you go to make sure that they are what you think they are.

When you've got it yourself, here's how we'd do it.

First, let's make an attempt to get all the values from our command line arguments, calculate the result, and print them out.

```javascript
let bill = process.argv[4];
let tipPercentage = process.argv[3];
let numGuests = process.argv[2];

let tipAmount = bill * tipPercentage;
let total = bill + tipAmount;
let amountOwedPerGuest = total / numGuests;

console.log("Each guest owes: $" + amountOwedPerGuest);
```

These are the right indexes if we're writing `node [filename] 2 25 150`, but there's a mistake somewhere—the printed result is `$NaN`. Go back and try to figure out where the issue arose. Log out those variable values and see where the problem came from!

One thing that might make this more obvious is to try to log out `typeof bill` or `typeof tipPercentage`, as well as `typeof tipAmount` and `typeof total`. This will print out `string` for the inputs we got form the user, and `number` for the variables we calculated.

Why is that? Think about it!

Well, Node isn't doing any magic to try to figure out whether the things we typed in were strings or booleans or numbers any of those. It just added them to the `process.argv` array as strings. When we tried to run math operations on those strings, we ended up with `NaN`, or "not a number".

So our last task is to convert those variables that came from the user to numbers. We'll also have to make sure to translate `25`, the tip percentage, to `0.25`—otherwise we're going to end up with an _awfully_ big tip.

Take a minute to figure it out on your own!

Here's the final result:

```javascript
let bill = Number(process.argv[4]);
let tipPercentage = Number(process.argv[3]) / 100;
let numGuests = Number(process.argv[2]);

let tipAmount = bill * tipPercentage;
let total = bill + tipAmount;
let amountOwedPerGuest = total / numGuests;

console.log("Each guest owes: $" + amountOwedPerGuest);
```

Now we've got a complete app that we can run at any time with any bill size, tip percentage, and number of people, and have it save us the headache of figuring out how to split those restaurant bills!

##### Takeaways From Your First Node Program

**JavaScript Has Different Tools In Node Than The Browser**

`process.argv` instead of `prompt` and `alert`, for sure, but we will also explore Node's ability to have files use other files, to listen for incoming network requests, and many other back-end-specific tools.

**There's Plenty Of New Infrastructure To Learn**

You are running code in the terminal for the first time, so you'll have to learn new commands, new workflows, and new tools.

But be patient with yourself—you've been here before, more than once. You succeeded in learning new tools before, and we're confident you will do so again.

**Programming Is (Still) Challenging**

Coding what seems like a simple problem still requires a great deal of in-depth thinking, breaking down the problem, debugging your solution, and testing that it works.

This is no different from more direct user interface code you've had to think through before. The environment is different, but JS and thinking algorithmically are no easier or harder in Node than the browser.

But if it were easy, you wouldn't need to learn it. And as John F. Kennedy said, "We choose to do [these things], not because they are easy, but because they are hard."

Happy hacking!
