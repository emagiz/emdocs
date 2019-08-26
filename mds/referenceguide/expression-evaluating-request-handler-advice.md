---
id: expression-evaluating-request-handler-advice
title: Expression evaluating request handler advice
sidebar_label: Expression evaluating request handler advice
---
#### Evaluates a configurable SpEL expression on successful and/or failed attempts.
This advice provides a mechanism to evaluate an expression on the original inbound message sent to the endpoint. Separate expressions are available to be evaluated, either after success, or failure. Optionally, a message containing the evaluation result, together with the input message, can be sent to a message channel.

A typical use case for this advice might be with an <i>FTP outbound channel adapter</i>, perhaps to move the file to one directory if the transfer was successful, or to another directory if it fails.

This advice has properties to set an expression when successful, an expression for failures, and corresponding channels for each. For the successful case, the message sent to the <i>success channel</i> is an <code>AdviceMessage</code>, with the payload being the result of the expression evaluation, and an additional property <code>inputMessage</code> which contains the original message sent to the handler. A message sent to the <i>failure channel</i> (when the handler throws an exception) is an <code>ErrorMessage</code> with a payload of <code>MessageHandlingExpressionEvaluatingAdviceException</code>. Like all <code>MessagingExceptions</code>, this payload has <code>failedMessage</code> and <code>cause</code> properties, as well as an additional property <code>evaluationResult</code>, containing the result of the expression evaluation.

#### On success expression
SpEL expression that will be executed on the input message when the message handler invocation was successful, for example <code>headers.file_originalFile.delete()</code>.

<i>Optional</i>

#### Success channel
If the <i>on success expression</i> evaluation returned a result (i.e. not 'null'; can also be an evaluation exception), an <code>AdviceMessage</code> is send to this message channel.

An <code>AdviceMessage</code> contains the evaluation result in its payload and the <code>inputMessage</code> <b>property</b> (i.e. Java class field; not a header!) contains the original message that was sent to the message handler.

Can only be used when the <i>on success expression</i> is specified.

<i>Optional</i>

#### On failure expression
SpEL expression that will be executed on the input message when the message handler invocation has failed, for example <code>headers.file_originalFile.renameTo(new java.io.File(${backup.dir} + '/' + headers.file_name))</code>.

<i>Optional</i>

#### Failure channel
If the <i>on failure expression</i> evaluation returned a result (i.e. not 'null'; can also be an evaluation exception), an <code>ErrorMessage</code> is send to this message channel.

The <code>ErrorMessage</code> will have a payload of type <code>MessageHandlingExpressionEvaluatingAdviceException</code>, which is a specialized <code>Exception</code> that also provides properties <code>failedMessage</code> (contains the original message that was sent to the message handler) and <code>evaluationResult</code> (contains the evaluation result of the on failure expression).

Can only be used when the <i>on failure expression</i> is specified.

Optional.

#### Trap exception
If <code>true</code>, any exception will be caught and <code>null</code> returned. This would basically prevent the normal error handling from being triggered, but can cause other errors to occur that will trigger the error handling anyway. For example, returning <code>null</code> in an <i>outbound gateway</i> with <i>requires reply</i> enabled, will result in a <code>ReplyRequiredException</code>.

Note that this does not cover exceptions that might occur while trying to evaluation the <i>on failure expression</i>. Whether or not it covers exceptions that might occur while trying to evaluation the <i>on success expression</i> is configurable with the <i>propagate evaluation failures</i> setting.

Default is <code>false</code>.

#### Return failure expression result
If <code>true</code>, the result of evaluating the <i>on failure expression</i> will be returned as the result instead of throwing an exception or returning <code>null</code>.

Note that the evaluation result can <i>also</i> be <code>null</code> or an evaluation exception.

Default is <code>false</code>.

#### Propagate evaluation failures
If <code>true</code> and an <i>on success expression</i> evaluation fails with an exception, the exception will be thrown to the caller. If <code>false</code>, the exception is caught.

Ignored for <i>on failure expression</i> evaluation: the original exception will be propagated (unless <i>trap exception</i> or <i>return failure expression result</i> is <code>true</code>).

Default is <code>false</code>.

---
id: expression-evaluating-request-handler-advice
title: Expression evaluating request handler advice
sidebar_label: Expression evaluating request handler advice
---
#### Evaluates a configurable SpEL expression on successful and/or failed attempts.
This advice provides a mechanism to evaluate an expression on the original inbound message sent to the endpoint. Separate expressions are available to be evaluated, either after success, or failure. Optionally, a message containing the evaluation result, together with the input message, can be sent to a message channel.

A typical use case for this advice might be with an <i>FTP outbound channel adapter</i>, perhaps to move the file to one directory if the transfer was successful, or to another directory if it fails.

This advice has properties to set an expression when successful, an expression for failures, and corresponding channels for each. For the successful case, the message sent to the <i>success channel</i> is an <code>AdviceMessage</code>, with the payload being the result of the expression evaluation, and an additional property <code>inputMessage</code> which contains the original message sent to the handler. A message sent to the <i>failure channel</i> (when the handler throws an exception) is an <code>ErrorMessage</code> with a payload of <code>MessageHandlingExpressionEvaluatingAdviceException</code>. Like all <code>MessagingExceptions</code>, this payload has <code>failedMessage</code> and <code>cause</code> properties, as well as an additional property <code>evaluationResult</code>, containing the result of the expression evaluation.

#### On success expression
SpEL expression that will be executed on the input message when the message handler invocation was successful, for example <code>headers.file_originalFile.delete()</code>.

<i>Optional</i>

#### Success channel
If the <i>on success expression</i> evaluation returned a result (i.e. not 'null'; can also be an evaluation exception), an <code>AdviceMessage</code> is send to this message channel.

An <code>AdviceMessage</code> contains the evaluation result in its payload and the <code>inputMessage</code> <b>property</b> (i.e. Java class field; not a header!) contains the original message that was sent to the message handler.

Can only be used when the <i>on success expression</i> is specified.

<i>Optional</i>

#### On failure expression
SpEL expression that will be executed on the input message when the message handler invocation has failed, for example <code>headers.file_originalFile.renameTo(new java.io.File(${backup.dir} + '/' + headers.file_name))</code>.

<i>Optional</i>

#### Failure channel
If the <i>on failure expression</i> evaluation returned a result (i.e. not 'null'; can also be an evaluation exception), an <code>ErrorMessage</code> is send to this message channel.

The <code>ErrorMessage</code> will have a payload of type <code>MessageHandlingExpressionEvaluatingAdviceException</code>, which is a specialized <code>Exception</code> that also provides properties <code>failedMessage</code> (contains the original message that was sent to the message handler) and <code>evaluationResult</code> (contains the evaluation result of the on failure expression).

Can only be used when the <i>on failure expression</i> is specified.

Optional.

#### Trap exception
If <code>true</code>, any exception will be caught and <code>null</code> returned. This would basically prevent the normal error handling from being triggered, but can cause other errors to occur that will trigger the error handling anyway. For example, returning <code>null</code> in an <i>outbound gateway</i> with <i>requires reply</i> enabled, will result in a <code>ReplyRequiredException</code>.

Note that this does not cover exceptions that might occur while trying to evaluation the <i>on failure expression</i>. Whether or not it covers exceptions that might occur while trying to evaluation the <i>on success expression</i> is configurable with the <i>propagate evaluation failures</i> setting.

Default is <code>false</code>.

#### Return failure expression result
If <code>true</code>, the result of evaluating the <i>on failure expression</i> will be returned as the result instead of throwing an exception or returning <code>null</code>.

Note that the evaluation result can <i>also</i> be <code>null</code> or an evaluation exception.

Default is <code>false</code>.

#### Propagate evaluation failures
If <code>true</code> and an <i>on success expression</i> evaluation fails with an exception, the exception will be thrown to the caller. If <code>false</code>, the exception is caught.

Ignored for <i>on failure expression</i> evaluation: the original exception will be propagated (unless <i>trap exception</i> or <i>return failure expression result</i> is <code>true</code>).

Default is <code>false</code>.

