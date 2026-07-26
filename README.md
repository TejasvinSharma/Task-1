# Task-1
The required solution is to implement:

def canonicalize(source: str) -> str:

using a hand-written parser (no parsing libraries).

Algorithm

1. Keep an index i over the string.
2. Create helper functions:
    * skip_ws()
    * peek()
    * expect(token)
    * parse_key()
    * parse_value()
3. Parse:

mission {
    member (; member)*
}

4. Store members in a dictionary.
5. If a key already exists → Duplicate key.
6. After parsing:
    * Sort keys alphabetically.
    * Remove _ from integers.
    * Print in canonical format.

parse_key()

* Read lowercase letters.
* If uppercase, digit or _ appears inside the key:

Error: Invalid key "<key>"

parse_value()

Handle four types:

1. Integer

* Read the entire [0-9_]+.
* Validate:
    * 0 is allowed.
    * No leading zero.
    * No leading/trailing _.
    * No consecutive _.
* Store after:

value.replace("_","")

2. String

* Starts with ".
* Read until next ".
* If newline/EOF first:

Error: Unterminated string

3. Boolean

* Only yes or no.

4. Crew ID

* Starts with @.
* Followed only by lowercase letters.

Member parsing

key = value

If = missing:

Error: Expected '=' after key "<key>"

Semicolon

After every member:

* If ;:
    * If next non-space character is }

Error: Trailing semicolon before '}'

    * Else parse next member.
* Otherwise expect }.

Canonical Output

For empty mission:

mission {}

Otherwise:

mission {
    commander = @alice;
    emergency = no;
    fuel = 4200;
    name = "Apollo-X"
}

where:

* keys are sorted,
* integers have _ removed,
* exactly one space around =,
* four-space indentation,
* semicolons only between entries.

This is the complete logic expected for the problem.
