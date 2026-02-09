# WordPress Claude Skills

A collection of [Claude AI skills](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/claude-ai-skills) for professional WordPress development. These skills ensure Claude follows official WordPress coding standards, security best practices, accessibility requirements (WCAG 2.1 AA), and WordPress.org directory guidelines when building plugins and themes.

## 🎯 What Are Claude Skills?

Claude Skills are reusable instruction sets that guide Claude's behavior for specific tasks. When you add these skills to your project, Claude automatically follows WordPress best practices — producing code that's secure, accessible, modular, and ready for WordPress.org submission.

## 📦 Included Skills

### 1. `wp-plugin-dev` — WordPress Plugin Development

Guides Claude to build production-ready WordPress plugins with proper architecture and security.

**Triggers when you say things like:**
- "Build me a plugin for X"
- "Create a WordPress plugin"
- "I need a WooCommerce extension"
- "Add a REST API endpoint"

**What it enforces:**

- **Clean bootstrap** — Main plugin file contains only constants, hooks, and autoloading. No feature logic.
- **Modular architecture** — Every feature gets its own class file (`includes/`, `admin/`, `public/`, `api/`)
- **Security** — Mandatory `sanitize_*()` on all input, `esc_*()` on all output, `$wpdb->prepare()` for all SQL, nonces on all forms, capability checks on all privileged actions
- **Caching** — Transients API and `wp_cache_*` for expensive operations
- **WordPress.org compliance** — GPL licensing, `readme.txt`, `uninstall.php`, proper prefixing, translatable strings

**Supported plugin types:**

| Type | Boilerplate Included |
|---|---|
| Standard (settings, CPTs, shortcodes) | ✅ |
| WooCommerce extensions | ✅ |
| Gutenberg block plugins | ✅ |
| REST API / headless plugins | ✅ |
| AJAX handlers | ✅ |
| Custom database tables | ✅ |

<details>
<summary><strong>File structure</strong></summary>

```
wp-plugin-dev/
├── SKILL.md                          # Main instructions (177 lines)
└── references/
    ├── architecture.md               # Boilerplate for all plugin types (742 lines)
    ├── security.md                   # Sanitization, escaping, $wpdb, nonces, caching (216 lines)
    └── wp-org-guidelines.md          # Condensed 18 official guidelines (31 lines)
```

</details>

---

### 2. `wp-theme-dev` — WordPress Theme Development

Guides Claude to build accessible, standards-compliant WordPress themes.

**Triggers when you say things like:**
- "Build me a theme for X"
- "Create a block theme"
- "I need a classic WordPress theme"
- "Make a child theme"

**What it enforces:**

- **Block themes as default** — Full Site Editing with `theme.json`, HTML templates, block patterns, style variations
- **Classic theme support** — Template hierarchy, The Loop, Customizer API when requested
- **Accessibility (WCAG 2.1 AA)** — Skip links, keyboard navigation, visible focus indicators, ARIA landmarks, 4.5:1 color contrast, underlined content links, proper heading hierarchy, screen-reader-text, reduced motion support
- **Modern CSS** — Custom properties, Grid/Flexbox, `clamp()` fluid typography, logical properties for RTL
- **WordPress.org compliance** — All 14 review categories, no plugin territory, proper licensing, `readme.txt` with resource credits

**Supported theme types:**

| Type | Boilerplate Included |
|---|---|
| Block themes (FSE) | ✅ |
| Classic PHP themes | ✅ |
| Child themes | ✅ |
| Hybrid themes | ✅ |

<details>
<summary><strong>File structure</strong></summary>

```
wp-theme-dev/
├── SKILL.md                              # Main instructions (193 lines)
└── references/
    ├── block-theme-architecture.md       # theme.json, templates, patterns, style variations (567 lines)
    ├── classic-theme-architecture.md     # Template hierarchy, The Loop, header/footer (497 lines)
    ├── accessibility.md                  # WCAG 2.1 AA + WordPress accessibility-ready (352 lines)
    └── review-requirements.md            # All 14 WordPress.org review categories (175 lines)
```

</details>

## 🚀 Installation

### For Claude Code (`.claude/` directory)

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/wordpress-claude-skills.git

# Copy skills to your project
cp -r wordpress-claude-skills/wp-plugin-dev your-project/.claude/skills/
cp -r wordpress-claude-skills/wp-theme-dev your-project/.claude/skills/
```

Your project structure should look like:

```
your-project/
└── .claude/
    └── skills/
        ├── wp-plugin-dev/
        │   ├── SKILL.md
        │   └── references/
        │       ├── architecture.md
        │       ├── security.md
        │       └── wp-org-guidelines.md
        └── wp-theme-dev/
            ├── SKILL.md
            └── references/
                ├── block-theme-architecture.md
                ├── classic-theme-architecture.md
                ├── accessibility.md
                └── review-requirements.md
```

### For Claude.ai (User Skills)

1. Download the skill folder(s) from this repo
2. Upload to Claude.ai via **Settings → Skills** (when available) or reference them in your project

## 💡 Usage Examples

### Plugin Development

```
Build me a WordPress plugin called "Smart Reviews" that adds a custom
post type for reviews with star ratings, a REST API endpoint to fetch
reviews, and a Gutenberg block to display them.
```

Claude will automatically:
- Scaffold a clean, modular plugin structure
- Keep the main file as a bootstrap loader only
- Create separate class files for the CPT, REST API, and block
- Sanitize all input, escape all output, use `$wpdb->prepare()`
- Generate `readme.txt` and `uninstall.php`

### Theme Development

```
Create a block theme called "Starter Blue" with a hero section,
blog archive, and dark mode style variation. Make it accessibility-ready.
```

Claude will automatically:
- Generate `theme.json` with accessible color palette (4.5:1+ contrast)
- Create HTML templates with proper semantic structure
- Add skip links, ARIA landmarks, underlined content links
- Include keyboard-navigable mobile menu with `aria-expanded`
- Build block patterns with translatable strings
- Generate `readme.txt` with resource credits

## 📚 Sources & References

These skills are built from official WordPress documentation:

- [WordPress Plugin Handbook](https://developer.wordpress.org/plugins/)
- [WordPress Plugin Guidelines](https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/)
- [WordPress Theme Handbook](https://developer.wordpress.org/themes/)
- [Theme Review Requirements](https://make.wordpress.org/themes/handbook/review/required/)
- [Accessibility-Ready Requirements](https://make.wordpress.org/themes/handbook/review/accessibility/required/)
- [WordPress Security APIs](https://developer.wordpress.org/apis/security/)
- [WCAG 2.1 Level AA](https://www.w3.org/WAI/WCAG21/quickref/?levels=aaa)

## 🤝 Contributing

Contributions are welcome! If you'd like to improve these skills:

1. Fork the repository
2. Create a feature branch (`git checkout -b improve-security-reference`)
3. Make your changes
4. Test with Claude to verify the skill produces correct output
5. Submit a pull request

**Areas that could use contributions:**
- Additional boilerplate patterns (e.g., WP-CLI commands, multisite support)
- Expanded Gutenberg block development patterns
- Performance optimization reference
- Testing/CI pipeline patterns

## 📄 License

This project is licensed under the [GPLv2 or later](https://www.gnu.org/licenses/gpl-2.0.html), consistent with WordPress itself.

## 👤 Author

**Mian** — Full-stack WordPress developer with 15+ years of experience.

- YouTube: [WP Academy](https://youtube.com/@wpacademy) (125K+ subscribers)
- Website: [msrbuilds.com](https://msrbuilds.com)
