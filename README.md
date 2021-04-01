# Languages Regex Benchmark (Optimized)

> This is an **optimized** version of the benchmark. It allows code and settings optimizations but keeping the measure, code style/structure and regex patterns.

It's just a simple regex benchmark for different programming languages.

Measures how long it takes to find and count non-overlapping occurrences.

> All benchmarks are wrong, but some are useful - [Szilard](https://github.com/szilard), [benchm-ml](https://github.com/szilard/benchm-ml)

I hope this benchmark can be helpful, but it's not only about performance, but each language also has its engine and offers different features (like UTF support, backreferences, capturing groups ...)

## Input text

The [input text](input-text.txt) is a concatenation of [Learn X in Y minutes](https://github.com/adambard/learnxinyminutes-docs) repository.

*Maybe isn't the best representative text. I'm searching other texts to add to the benchmark.*

## Regex patterns

- Email: ``[\w\.+-]+@[\w\.-]+\.[\w\.-]+``
- URI: ``[\w]+://[^/\s?#]+[^\s?#]+(?:\?[^\s#]*)?(?:#[^\s]*)?``
- IPv4: ``(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9])\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9])``

The above regex patterns aren't the best or the optimal. The focus is the benchmark, not the matching.

The patterns are applied to the whole file.

## Measure

Measuring is done inside the programs to avoid include startup, reading and writing times on results.

Elapsed time include pattern compilation, find and count occurrences.

## Performance

> The following results are for the optimized version. [Go to default version](https://github.com/mariomka/regex-benchmark/tree/master).

Docker image was run on: MacBook Pro (Retina, 15-inch, 2017), 2.8 GHz Intel Core i7, 16 GB 1600 Mhz DDR3 with macOS Catalina 10.15.3.

Language | Email(ms) | URI(ms) | IP(ms) | Total(ms)
--- | ---: | ---: | ---: | ---:
**Rust** | 16.42 | 15.54 | 6.90 | 38.86
**C PCRE2** | 30.94 | 27.14 | 6.43 | 64.52
**PHP** | 28.79 | 27.81 | 9.15 | 65.74
**Nim** | 28.56 | 28.37 | 9.20 | 66.13
**Javascript** | 80.64 | 66.53 | 2.08 | 149.25
**C++ Boost** | 90.57 | 90.59 | 30.51 | 211.68
**Perl** | 119.25 | 84.61 | 54.35 | 258.22
**Dart** | 159.45 | 154.45 | 147.60 | 461.50
**Crystal** | 312.54 | 276.46 | 24.19 | 613.19
**Python PyPy2** | 215.31 | 198.09 | 369.29 | 782.69
**D dmd** | 383.71 | 398.64 | 10.34 | 792.69
**Ruby** | 425.79 | 375.77 | 69.13 | 870.70
**D ldc** | 447.77 | 452.37 | 9.33 | 909.48
**Python PyPy3** | 351.28 | 311.91 | 358.64 | 1021.84
**Go** | 341.41 | 344.39 | 523.33 | 1209.13
**Java** | 263.55 | 314.37 | 719.25 | 1297.17
**Kotlin** | 279.78 | 312.16 | 715.65 | 1307.58
**Python 2** | 974.39 | 330.55 | 1200.23 | 2505.17
**C++ STL** | 867.84 | 743.66 | 937.08 | 2548.58
**Python 3** | 1122.67 | 398.51 | 1206.83 | 2728.01
**C# .Net Core** | 2329.68 | 2005.52 | 143.48 | 4478.68
**Dart Native** | 2116.81 | 2396.46 | 38.58 | 4551.85
**C# Mono** | 2384.82 | 1991.34 | 216.20 | 4592.36

- **Language**: Indicates the language.
- **Email(ms)**, **URI(ms)**, **IP(ms)**: Indicates the time elapsed in milliseconds for finding and counting non-overlapping occurrences for the pattern.
- **Total(ms)**: Indicates the sum of the above times.

### Versions and notes

- **C**: gcc 7.5.0 & PCRE2 10.36-2
- **Crystal**: crystal 0.35.1 - LLVM: 8.0.0
- **C++**: g++ 7.5.0 | Boost 1.65.1.0
- **C#**: dotnet 5.0.201 | Mono 6.12.0.122
- **D**: DMD v2.089.0 | LDC 1.8.0
- **Dart**: Dart 2.12.2
- **Go**: go 1.16.2
- **Java**: OpenJDK 11.0.10
- **Javascript**: node v15.13.0
- **Julia**: Julia 1.6.0
- **Kotlin**: kotlinc-jvm 1.4.32
- **Nim**: Nim 1.4.4
- **Perl**: perl v5.26.1
- **PHP**: PHP 8.0.3
- **Python**: Python 2.7.17 | Python 3.6.9 | PyPy 7.3.3
- **Ruby**: ruby 2.5.1p57
- **Rust**: rustc 1.51.0 & regex 1.4.5

# How to run

The easiest way to run the benchmark is by using Docker.

```sh
git clone https://github.com/mariomka/regex-benchmark.git
git checkout optimized
cd regex-benchmark
docker run --rm -v $(pwd):/var/regex mariomka/regex-benchmark:1.6
```

# Contributing

All contributions are welcome, from tiny optimizations to new implementations.

There are only a few requirements:
- Follow the style of the current implementations
- Update `Dockerfile` if it's necessary

# Kudos

- Heng Li's for his work on [Benchmark of Regex Libraries](http://lh3lh3.users.sourceforge.net/reb.shtml).
- A "challenge" on [Madrid Devs](http://madriddevs.org/) group inspired me.
- [Programming subreddit](https://www.reddit.com/r/programming/), helped me to improve the benchmark.

# License

MIT © [Mario Juárez](https://github.com/mariomka).
