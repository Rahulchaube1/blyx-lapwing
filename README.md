<img src="assets/logo.png" width="112" height="112" alt="A green-winged lapwing looks back beneath a long swept crest.">

# Lapwing

Preflight fixed-line document pagination with indivisible paragraphs. This Blyx workflow framework is part of the documents, images and media collection.

A report can fit in aggregate yet overflow when a paragraph must stay together. Pack the measured paragraphs into the usable page area. [W3C, CSS fragmentation](https://www.w3.org/TR/css-break-3/)

## Editor extension

Install **RahulChaube.blyx-lapwing** to run the worked example and use the framework’s function completions in a Blyx file. Open an empty `.blyx` file, enter `blyx-lapwing-demo`, then choose **Blyx: Run File**. [Editor downloads](https://www.blyx-lang.space/packages/lapwing#editor) · [Download the extension](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-lapwing-0.1.0.vsix) · [Starter with framework source](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-lapwing-starter-0.1.0.zip)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-lapwing.git
cd blyx-lapwing
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-lapwing) · [Package page](https://www.blyx-lang.space/packages/lapwing) · [Handbook](https://doc.blyx-lang.space/guide/lapwing)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-lapwing.git vendor/lapwing
```

```blyx
use vendor::lapwing::lapwing;

fn main() {
    let blocks = [4, 6, 3];
    let paper = 120.0;
    let top = 10.0;
    let bottom = 10.0;
    let line = 10.0;
    let result = lapwing_paginate(blocks, paper, top, bottom, line);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
2
3
7
10
```

## API

`lapwing_paginate(blocks, paper, top, bottom, line)`

Returns [pages, lines used on final page, unused line slots, printable lines per page]. Blocks are positive paragraph line counts. The host measures text and renders the resulting pages. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| blocks | Vector of values, each a nonnegative exact integer |
| paper | A positive finite number |
| top | A nonnegative finite number |
| bottom | A nonnegative finite number |
| line | A positive finite number |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "4,6,3" 120 10 10 10
```

## Libraries

- [PageBreaks](https://github.com/Rahulchaube1/blyx-pagebreaks/tree/v0.1.0) — Place unsplittable document blocks on successive pages in input order.
- [LineFit](https://github.com/Rahulchaube1/blyx-linefit/tree/v0.1.0) — Compute the usable print area and whole lines per page.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-lapwing/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The [artwork notice](assets/NOTICE.txt) records credits for earlier editions.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
