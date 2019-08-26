---
id: generate-flat-file-definition-based-on-comma-separated-values
title: Generate flat file definition based on comma separated values
sidebar_label: Generate flat file definition based on comma separated values
---
#### Names
Column names (comma separated). Optional, but if set, then all lines must have as many or fewer tokens.

No column names are set by default.

If this tokenizer is used in combination with an <i>XML field set mapper</i> this property is <b>required</b> and has the following additional restrictions:
- Every column name must be a valid (non-colonized) XML name.
- At most one column name may be equal to the special token <code>*RECORD_TYPE*</code>: the <i>value</i> of such a column will then be used as the name for the record (or root) XML element containing the columns. This value will be prefixed with an underscore if needed, but otherwise must be a valid XML name. The column itself will then be excluded from the resulting XML.

#### Columns
The column ranges. 

This property can be set in the form of a String describing the range boundaries, e.g. "1,4,7" or "1-3,4-6,7" or "1-2,4-5,7-10". If the last range is open then the rest of the line is read into that column (irrespective of the strict flag setting).

Required.

#### Names
Column names (comma separated). Optional, but if set, then all lines must have as many or fewer tokens.

No column names are set by default.

If this tokenizer is used in combination with an <i>XML field set mapper</i> this property is <b>required</b> and has the following additional restrictions:
- Every column name must be a valid (non-colonized) XML name.
- At most one column name may be equal to the special token <code>*RECORD_TYPE*</code>: the <i>value</i> of such a column will then be used as the name for the record (or root) XML element containing the columns. This value will be prefixed with an underscore if needed, but otherwise must be a valid XML name. The column itself will then be excluded from the resulting XML.

#### Columns
The column ranges. 

This property can be set in the form of a String describing the range boundaries, e.g. "1,4,7" or "1-3,4-6,7" or "1-2,4-5,7-10". If the last range is open then the rest of the line is read into that column (irrespective of the strict flag setting).

Required.

---
id: generate-flat-file-definition-based-on-comma-separated-values
title: Generate flat file definition based on comma separated values
sidebar_label: Generate flat file definition based on comma separated values
---
#### Names
Column names (comma separated). Optional, but if set, then all lines must have as many or fewer tokens.

No column names are set by default.

If this tokenizer is used in combination with an <i>XML field set mapper</i> this property is <b>required</b> and has the following additional restrictions:
- Every column name must be a valid (non-colonized) XML name.
- At most one column name may be equal to the special token <code>*RECORD_TYPE*</code>: the <i>value</i> of such a column will then be used as the name for the record (or root) XML element containing the columns. This value will be prefixed with an underscore if needed, but otherwise must be a valid XML name. The column itself will then be excluded from the resulting XML.

#### Columns
The column ranges. 

This property can be set in the form of a String describing the range boundaries, e.g. "1,4,7" or "1-3,4-6,7" or "1-2,4-5,7-10". If the last range is open then the rest of the line is read into that column (irrespective of the strict flag setting).

Required.

#### Names
Column names (comma separated). Optional, but if set, then all lines must have as many or fewer tokens.

No column names are set by default.

If this tokenizer is used in combination with an <i>XML field set mapper</i> this property is <b>required</b> and has the following additional restrictions:
- Every column name must be a valid (non-colonized) XML name.
- At most one column name may be equal to the special token <code>*RECORD_TYPE*</code>: the <i>value</i> of such a column will then be used as the name for the record (or root) XML element containing the columns. This value will be prefixed with an underscore if needed, but otherwise must be a valid XML name. The column itself will then be excluded from the resulting XML.

#### Columns
The column ranges. 

This property can be set in the form of a String describing the range boundaries, e.g. "1,4,7" or "1-3,4-6,7" or "1-2,4-5,7-10". If the last range is open then the rest of the line is read into that column (irrespective of the strict flag setting).

Required.

