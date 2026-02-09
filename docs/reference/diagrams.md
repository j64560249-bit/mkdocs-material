---
icon: material/graph-outline
---

# Diagrams

Diagrams help to communicate complex relationships and interconnections between
different technical components, and are a great addition to project
documentation. Material for MkDocs integrates with [Mermaid.js], a very
popular and flexible solution for drawing diagrams.

  [Mermaid.js]: https://mermaid.js.org/

## Configuration

<!-- md:version 8.2.0 -->

This configuration enables native support for [Mermaid.js] diagrams. Material
for MkDocs will automatically initialize the JavaScript runtime when a page
includes a `mermaid` code block:

``` yaml
markdown_extensions:
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
```

No further configuration is necessary. Advantages over a custom integration:

- [x] Works with [instant loading] without any additional effort
- [x] Diagrams automatically use fonts and colors defined in `mkdocs.yml`
    sequence diagrams, class diagrams, state diagrams and entity relationship
    diagrams. See the section on [other diagrams] for more information why this
    is currently not implemented for all diagrams.

  [instant loading]: ../setup/setting-up-navigation.md#instant-loading
  [additional style sheets]: ../customization.md#additional-css
  [other diagrams]: #other-diagram-types

## Usage

### Using flowcharts

[Flowcharts] are diagrams that represent workflows or processes. The steps
are rendered as nodes of various kinds and are connected by edges, describing
the necessary order of steps:

```` markdown title="Flow chart"
``` mermaid
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```
````

<div class="result" markdown>

``` mermaid
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```

</div>

  [Flowcharts]: https://mermaid.js.org/syntax/flowchart.html

### Using sequence diagrams

[Sequence diagrams] describe a specific scenario 
sequenceDiagram
  autonumber
  Alice->>John: Hello John, how are you?
  loop Healthcheck
      John->>John: Fight against hypochondria
  end
  Note right of John: Rational thoughts!
  John-->>Alice: Great!
  John->>Bob: How about you?
  Bob-->>John: Jolly good!
```
````

<div class="result" markdown>

``` mermaid
sequenceDiagram
  autonumber
  Alice->>John: Hello John, how are you?
  loop Healthcheck
      John->>John: Fight against hypochondria
  end
  Note right of John: Rational thoughts!
  John-->>Alice: Great!
  John->>Bob: How about you?
  Bob-->>John: Jolly good!
```

</div>

  [Sequence diagrams]: https://mermaid.js.org/syntax/sequenceDiagram.html

### Using state diagrams

[State diagrams] are a great tool to describe the behavior of a system,
decomposing it into a finite number of states, and transitions between those
states:

```` markdown title="State diagram"
``` mermaid
stateDiagram-v2
  state fork_state <<fork>>
    [*] --> fork_state
    fork_state --> State2
    fork_state --> State3

    state join_state <<join>>
    State2 --> join_state
    State3 --> join_state
    join_state --> State4
    State4 --> [*]
```
````

<
