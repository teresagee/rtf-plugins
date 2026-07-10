# rtf-plugins

Teresa's merged Claude Code plugin marketplace. Five custom plugins, each combining an
older `cws-*` plugin with its newer v1.0.2+ counterpart into a single snapshot.

> These are **custom snapshots** — they do not auto-update from Alex McFarland anymore.
> That's expected and accepted.

## Plugins

| Plugin | Skills | Combines |
| --- | --- | --- |
| `substack-all` | 16 | cws-substack + substack (v1.0.2) |
| `linkedin-all` | 7 | cws-linkedin + linkedin (v1.0.2) |
| `research-all` | 11 | cws-research + research (v1.0.2) |
| `landing-pages-all` | 5 | cws-landing-page + landing-pages (v1.0.2) |
| `digital-products-all` | 6 | digital-products (v1.0.4) + cws-ebook |

## Install

```
/plugin marketplace add teresagee/rtf-plugins
/plugin install substack-all@rtf-plugins
/plugin install linkedin-all@rtf-plugins
/plugin install research-all@rtf-plugins
/plugin install landing-pages-all@rtf-plugins
/plugin install digital-products-all@rtf-plugins
```

Commands are namespaced by plugin, e.g. `substack-all:tips`, `linkedin-all:linkedin-post`.

## Notes on merge conflicts

- **substack-all** — `welcome-sequence` existed in both; kept the v1.0.2 version, dropped the cws one.
- **landing-pages-all** — `build-page` existed in both; kept the v1.0.2 version, dropped the cws one.
- **substack-all** keeps both `notes` (new) and `substack-note` (old) — similar but distinct.

## Voice plugins (Part 2)

```
/plugin install voices@rtf-plugins
/plugin install voice-creation@rtf-plugins
```

`voices` is Teresa's own voice profiles (self, storyteller, coach; aiinn and rtf brand voices pending). `voice-creation` is Alex McFarland's v1.2.4 republished with a flattened structure and repaired skill frontmatter, fixing the broken nested install.
