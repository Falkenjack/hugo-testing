+++
title = 'Hugo Forum Topic #53952'
linkTitle = 'Home'
date = 2025-03-14T16:21:18-07:00
draft = false
details = 'https://discourse.gohugo.io/t/53952'
description = "Code in highlight shortcode rendered as markdown"
+++

# 1 Without nesting or include

Works but I want to be able to nest.

{{< highlight python "hl_inline=true, lineNumbersInTable=false" >}}def __init__(self, args):{{< /highlight >}} (using `{{</* highlight python "hl_inline=true, lineNumbersInTable=false" */>}}`)




<hr>

# 2 With nesting {#2}

## 2.1 Only standard shortcodes

Code is rendered as code, but markdown never rendered inside `acc`?

{{< acc >}}

## Heading for accordion cell

{{< div >}}

_Content of accordion cell containing markdown, possibly code blocks and inline code as below._

{{< highlight python "hl_inline=true, lineNumbersInTable=false" >}}def __init__(self, args):{{< /highlight >}} (using `{{</* highlight python "hl_inline=true, lineNumbersInTable=false" */>}}`)

```python
def __init__(self, args):
    """This method is called when the class is instantiated."""
    self.args = args
```

{{< /div >}}

{{< /acc >}}





<hr>

## 2.2 Markdown shortcodes everywhere (obv. wrong for inline code but sanity check)

Code rendered as markdown first, then as code, then everything (including code) is rendered as markdown?

{{% acc %}}

## Heading for accordion cell

{{< div >}}

_Content of accordion cell containing markdown, possibly code blocks and inline code as below._

{{% highlight python "hl_inline=true, lineNumbersInTable=false" %}}def __init__(self, args):{{% /highlight %}} (using `{{%/* highlight python "hl_inline=true, lineNumbersInTable=false" */%}}`)

```python
def __init__(self, args):
    """This method is called when the class is instantiated."""
    self.args = args
```

{{% /div %}}

{{% /acc %}}





<hr>

## 2.3 Markdown shortcodes everywhere except for the inline code {#2.3}

Code is rendered as code, then everything (including code) is rendered as markdown?

{{% acc %}}

## Heading for accordion cell

{{< div >}}

_Content of accordion cell containing markdown, possibly code blocks and inline code as below._

{{< highlight python "hl_inline=true, lineNumbersInTable=false" >}}def __init__(self, args):{{< /highlight >}} (using `{{</* highlight python "hl_inline=true, lineNumbersInTable=false" */>}}`)

```python
def __init__(self, args):
    """This method is called when the class is instantiated."""
    self.args = args
```

{{% /div %}}

{{% /acc %}}






<hr>

## 2.4 Markdown shortcode only for `acc`, standard shortcode for `div` and inline code

Same as [2.3](#2.3)?

{{% acc %}}

## Heading for accordion cell

{{< div >}}

_Content of accordion cell containing markdown, possibly code blocks and inline code as below._

{{< highlight python "hl_inline=true, lineNumbersInTable=false" >}}def __init__(self, args):{{< /highlight >}} (using `{{</* highlight python "hl_inline=true, lineNumbersInTable=false" */>}}`)

```python
def __init__(self, args):
    """This method is called when the class is instantiated."""
    self.args = args
```

{{< /div >}}

{{% /acc %}}






<hr>

# 3 With `include` but without nesting

### Icluded using `{{%/* include "file_to_include.md" */%}}`

Code is rendered as code, markdown is rendered as markdown, but I want to be able to nest.

{{% include "file_to_include.md" %}}

### Icluded using `{{</* include "file_to_include.md" */>}}`

Code is rendered as code, markdown is never rendered?

{{< include "file_to_include.md" >}}






<hr>

# 4 With `include` and nesting

### Icluded using `{{%/* include "acc_to_include.md" */%}}`

Behavior depending on types of shortcodes used in included file, seems identical to behaviors in [2](#2)? I.e. it doesn't seem as if `include` affects the issue.

{{% include "acc_to_include.md" %}}

### Icluded using `{{</* include "acc_to_include.md" */>}}`

Code is rendered as code, markdown is never rendered?

{{< include "acc_to_include.md" >}}
