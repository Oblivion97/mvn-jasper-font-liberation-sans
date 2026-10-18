# mvn-jasper-font-liberation-sans

[![CI](https://github.com/Oblivion97/mvn-jasper-font-liberation-sans/actions/workflows/ci.yml/badge.svg)](https://github.com/Oblivion97/mvn-jasper-font-liberation-sans/actions/workflows/ci.yml)

**Liberation Sans**, a free replacement for **Arial**, packaged as a JasperReports font extension and registered under the family name `Arial`.

Add it as a Maven dependency and [JasperReports](https://community.jaspersoft.com/) finds the font automatically. You
don't need to install fonts on the server or copy files, and the font is embedded in exported PDFs.

| | |
|---|---|
| Font | Liberation Sans 2.1.5 (regular, bold, italic, bold italic) |
| Registered family names | `Arial`, `Liberation Sans` |
| Font license | SIL Open Font License 1.1 |

## Use it

Add the repository and the dependency to your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>oblivion-liberation-sans-github</id>
        <url>https://raw.githubusercontent.com/Oblivion97/mvn-jasper-font-liberation-sans/main/</url>
        <snapshots><enabled>false</enabled></snapshots>
    </repository>
</repositories>

<dependency>
    <groupId>io.github.oblivion97</groupId>
    <artifactId>jasper-font-liberation-sans</artifactId>
    <version>1.0.0</version>
</dependency>
```

Then use the family name in your report, for example `fontName="Arial"`.

## Replacing Arial

Arial's license doesn't allow redistribution, so it can't be packaged. Liberation Sans was designed with the same
character widths (metrics) as Arial, so text takes the same space and report layouts don't shift. Because this package
also registers it as `Arial`, existing reports work unchanged. If your project also bundles the real Arial as a font
extension, remove it, so the family name is registered only once. Letter shapes differ slightly, so check a few
reports after switching.

## How it works

The jar contains a `jasperreports_extension.properties` file. At startup, JasperReports scans the classpath for these
files and registers the font families they list. The font files live under `io/github/oblivion97/fonts/…`, so they
don't clash with other font jars. A test renders a real PDF with JasperReports 6.20 and checks that the font is
embedded.

## Credits and license

The font files are distributed **unmodified**, and the jar includes the font's license under `META-INF/`.

- **Liberation Sans:** copyright © 2012 Red Hat, Inc., with Reserved Font Name *Liberation*; digitized data copyright
  © 2010 Google Corporation. Licensed under the [SIL Open Font License 1.1](https://spdx.org/licenses/OFL-1.1.html);
  the full text is in `META-INF/LICENSE-OFL-1.1.txt`. Source:
  [liberationfonts/liberation-fonts](https://github.com/liberationfonts/liberation-fonts).

*Liberation* is a trademark of Red Hat, Inc. *Arial* is a trademark of The Monotype Corporation. This package isn't
affiliated with or endorsed by either, and doesn't contain Arial; the `Arial` family name is a compatibility alias.

The build files in this repository (pom, tests, workflows, scripts) are under the [MIT License](LICENSE).

## Releasing

See [RELEASING.md](RELEASING.md).
