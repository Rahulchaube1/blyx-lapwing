## Paginate a report with indivisible paragraphs

Returns [pages, lines used on final page, unused line slots, printable lines per page]. Blocks are positive paragraph line counts. The host measures text and renders the resulting pages. Invalid arguments and nonfinite results return an empty vector.

1. Open an empty file named `lapwing-demo.blyx`.
2. Type `blyx-lapwing-demo` and select **Lapwing — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
2
3
7
10
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-lapwing)
