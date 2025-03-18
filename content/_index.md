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

{{< pyline >}}def __init__(self, args):{{< /pyline >}} (using `{{</* pyline */>}}`)

```python
def __init__(self, args):
    """This method is called when the class is instantiated."""
    self.args = args
```


<hr>

## 2.3 Markdown shortcodes everywhere except for the inline code {#2.3}

{{% acc %}}

## Heading for accordion cell

{{< div >}}

_Content of accordion cell containing markdown, possibly code blocks and inline code as below._

{{< pyline >}}def __init__(self, args):{{< /pyline >}} (using `{{</* pyline */>}}`)

```python
def __init__(self, args):
    """This method is called when the class is instantiated."""
    self.args = args
```

{{% /div %}}

{{% /acc %}}




<hr>

# 4 With `include` and nesting

### Icluded using `{{%/* include "acc_to_include.md" */%}}`

{{% include "acc_to_include.md" %}}
