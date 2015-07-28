FAQ:
====
Why?
----
Because it's a Tuesday night in South Dakota?

Should I actually use this?
---------------------------
Probably not.

Why isn't this ANSI SQL?
------------------------
Because supporting parsing actual SQL in bash is beyond the scope of a couple hour project (for me).


Supported SQL(ish) Syntax:
==========================

SELECT
------
	'SELECT' column_expr[, column_expr...]
	['FROM' table_name]
	['WHERE' bool_expression]
	['GROUPBY' column_expr] ';'

INSERT
------
	'INSERT' ['INTO'] table_name
	'(' column_expr[, column_expr...] ')'
	'VALUES '(' value_expr[, value_expr...] ')';

UPDATE
------
	'UPDATE' table_name SET
	column_name '=' value_expr[, column_name '=' value_expr]
	['WHERE' bool_expr] ';'

DELETE
------
	'DELETE FROM' table_name
	['WHERE' bool_expr] ';'

table_name  := identifier

column_name := identifier

column_expr := column_name | value_expr

value_expr  := '"' value_text '"'

value_text  :~ ([^"\]|\\|\")\*

bool_expr   := value_expr equal_op value_expr [(AND | OR) bool_expr]

equal_op    := = | < | > | <= | >= | <>

identifier  :~ [A-Za-z0-9_]+

