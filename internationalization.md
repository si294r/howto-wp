## Internationalization and locale handling

1. Install PoEdit
    - https://poedit.net/
      
2. Default locale = `id_ID`
   
3. Use file `[plugins-foler]/[plugin-name]/languages/template.pot`, ex:
   
```
msgid ""
msgstr ""
"Project-Id-Version: \n"
"POT-Creation-Date: \n"
"PO-Revision-Date: \n"
"Last-Translator: \n"
"Language-Team: \n"
"Report-Msgid-Bugs-To: \n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Plural-Forms: nplurals=2; plural=n != 1;\n"
"X-Textdomain-Support: yes\n"
"X-Poedit-SourceCharset: UTF-8\n"
"X-Poedit-KeywordsList: __;_e;esc_html_e;esc_html_x:1,2c;esc_html__;esc_attr_e;esc_attr_x:1,2c;esc_attr__;_ex:1,2c;_nx:4c,1,2;_nx_noop:4c,1,2;_x:1,2c;_n:1,2;_n_noop:1,2;__ngettext:1,2;__ngettext_noop:1,2;_c,_nc:4c,1,2;\n"
"X-Poedit-Basepath: ../\n"
"X-Poedit-SearchPath-0: .\n"
"X-Poedit-SearchPathExcluded-0: vendor\n"
```

4. Add minimum english-US translation, necessary for presentations with foreign people (investors)

