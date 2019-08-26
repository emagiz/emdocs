---
id: thclient-connector
title: ThClient connector
sidebar_label: ThClient connector
---
#### Connects to ThClient databases through 'thclient.dll' using Java Native Access (JNA).
Connects to ThClient databases through <code>thclient.dll</code> using Java Native Access (JNA). Exposes methods for reading full tables and reading only the changed records.

One instance of this support object will only ever use one concurrent database connection.

#### ThClient DLL path
The <b>path to the directory</b> where the <code>thclient.dll</code> native library can be found, for example <code>"C:/Intramed"</code>.

Note that JNA will search the directory automatically for a native library named "thclient" that is compatible with the current system architecture. This means that in order to load the 32-bit Windows "thclient.dll" library, you'll need to run eMagiz in a 32-bit Windows JVM (even if the operating system is 64-bit).

<i>Required</i>

#### Charset
Character set that is used by <code>thclient.dll</code> to encode string values.

When connecting with <i>Intramed</i>, you should probably set this property to <code>Cp1252</code>.

Default is <code>UTF-8</code>.

#### Server name
The name of the server to connect with, for example <code>"intramed.exe"</code>.

<i>Required</i>

#### Use log table
Whether you want use the log table of the ThClient database.

If you want to use the <i>ThClient changes reading activator</i> with this connector, this setting must be enabled.


The table definitions for this connector configuration.

<i>Required</i>


A log table keeps track of changes in the ThClient database. For every change it adds a record to this table identifying the type of the log item and the index values of the records that were changed. In which table these records can be found is defined by the log item type.

#### Code
The (unique) code of the log table.

This number should be copied from the database definition of the ThClient application.

<i>Required</i>

#### Name
The (unique) name for the log table.

Used to indentify this definition when referencing it from a message but never actually used for communicating with the ThClient database, so you can make up your own (unique) values.

<i>Required</i>

#### Index columns
The index column code(s) of the log table.

This number (or numbers in case of a multi-column index) should be copied from the database definition of the ThClient application.

<i>Required</i>

#### Log item type column
The code of the column containing the log item type in the log table.

This number should be copied from the database definition of the ThClient application.

<i>Required</i>

#### Object columns
The (comma separated) codes of the columns containing the object references in the log table.

These numbers should be copied from the database definition of the ThClient application.

<i>Required</i>


The mappings between log item types and the corresponding table codes.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: thclient-connector
title: ThClient connector
sidebar_label: ThClient connector
---
#### Connects to ThClient databases through 'thclient.dll' using Java Native Access (JNA).
Connects to ThClient databases through <code>thclient.dll</code> using Java Native Access (JNA). Exposes methods for reading full tables and reading only the changed records.

One instance of this support object will only ever use one concurrent database connection.

#### ThClient DLL path
The <b>path to the directory</b> where the <code>thclient.dll</code> native library can be found, for example <code>"C:/Intramed"</code>.

Note that JNA will search the directory automatically for a native library named "thclient" that is compatible with the current system architecture. This means that in order to load the 32-bit Windows "thclient.dll" library, you'll need to run eMagiz in a 32-bit Windows JVM (even if the operating system is 64-bit).

<i>Required</i>

#### Charset
Character set that is used by <code>thclient.dll</code> to encode string values.

When connecting with <i>Intramed</i>, you should probably set this property to <code>Cp1252</code>.

Default is <code>UTF-8</code>.

#### Server name
The name of the server to connect with, for example <code>"intramed.exe"</code>.

<i>Required</i>

#### Use log table
Whether you want use the log table of the ThClient database.

If you want to use the <i>ThClient changes reading activator</i> with this connector, this setting must be enabled.


The table definitions for this connector configuration.

<i>Required</i>


A log table keeps track of changes in the ThClient database. For every change it adds a record to this table identifying the type of the log item and the index values of the records that were changed. In which table these records can be found is defined by the log item type.

#### Code
The (unique) code of the log table.

This number should be copied from the database definition of the ThClient application.

<i>Required</i>

#### Name
The (unique) name for the log table.

Used to indentify this definition when referencing it from a message but never actually used for communicating with the ThClient database, so you can make up your own (unique) values.

<i>Required</i>

#### Index columns
The index column code(s) of the log table.

This number (or numbers in case of a multi-column index) should be copied from the database definition of the ThClient application.

<i>Required</i>

#### Log item type column
The code of the column containing the log item type in the log table.

This number should be copied from the database definition of the ThClient application.

<i>Required</i>

#### Object columns
The (comma separated) codes of the columns containing the object references in the log table.

These numbers should be copied from the database definition of the ThClient application.

<i>Required</i>


The mappings between log item types and the corresponding table codes.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

