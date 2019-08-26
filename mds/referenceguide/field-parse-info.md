---
id: field-parse-info
title: Field parse info
sidebar_label: Field parse info
---
#### Field number
Field number (in the range 2 - 127).

#### ISO type
Type of the field parse info to create:
<code>ALPHA</code> - a fixed-length alphanumeric value, filled with spaces to the right
<code>AMOUNT</code> - an amount, expressed in cents with a fixed length of 12
<code>BINARY</code> - similar to ALPHA but holds byte arrays instead of strings
<code>DATE10</code> - a date in format <i>MMddHHmmss</i>
<code>DATE4</code> - a date in format <i>MMdd</i>
<code>DATE_EXP</code> - (expiration) date in format <i>yyMM</i>
<code>LLBIN</code> - similar to LLVAR but holds byte arrays instead of strings
<code>LLLBIN</code> - similar to LLLVAR but holds byte arrays instead of strings
<code>LLLVAR</code> - a variable length alphanumeric value with a 3-digit header length
<code>LLVAR</code> - a variable length alphanumeric value with a 2-digit header length
<code>NUMERIC</code> - a fixed-length numeric value, zero-filled to the left
<code>TIME</code> - time of day in format <i>HHmmss</i>

If the field should be parsed using a custom field encoder/decoder, it must be one of the following types: ALPHA, LLVAR, LLLVAR, BINARY, LLBIN or LLLBIN.

#### Length
Length of the field (must be 1 or greater).

---
id: field-parse-info
title: Field parse info
sidebar_label: Field parse info
---
#### Field number
Field number (in the range 2 - 127).

#### ISO type
Type of the field parse info to create:
<code>ALPHA</code> - a fixed-length alphanumeric value, filled with spaces to the right
<code>AMOUNT</code> - an amount, expressed in cents with a fixed length of 12
<code>BINARY</code> - similar to ALPHA but holds byte arrays instead of strings
<code>DATE10</code> - a date in format <i>MMddHHmmss</i>
<code>DATE4</code> - a date in format <i>MMdd</i>
<code>DATE_EXP</code> - (expiration) date in format <i>yyMM</i>
<code>LLBIN</code> - similar to LLVAR but holds byte arrays instead of strings
<code>LLLBIN</code> - similar to LLLVAR but holds byte arrays instead of strings
<code>LLLVAR</code> - a variable length alphanumeric value with a 3-digit header length
<code>LLVAR</code> - a variable length alphanumeric value with a 2-digit header length
<code>NUMERIC</code> - a fixed-length numeric value, zero-filled to the left
<code>TIME</code> - time of day in format <i>HHmmss</i>

If the field should be parsed using a custom field encoder/decoder, it must be one of the following types: ALPHA, LLVAR, LLLVAR, BINARY, LLBIN or LLLBIN.

#### Length
Length of the field (must be 1 or greater).

