# MCBE-Addon-Translation-Github-Action

This GitHub Actions workflow automatically translates your Minecraft Bedrock add-on every time you push code. It also helps with manual translations by creating `TODO: Translate the following {source_text}` comments.<br >
Just add the files in the `.github` folder to your repository and you're all set!

> [!NOTE]
> This script assumes the branch contains the root of either a behavior or resource pack.<br>
> If the structure of your repo is different, you must change the source and target directories.

## Config
Head over to `.github/scripts/auto_translate_config.yaml`
```yaml
source: texts/en_US.lang # the source language file to translate
destination: texts/ # the destination folder for translated files
target_langs_auto: ['es_MX', 'es_ES', 'de_DE'] # languages to auto-translate
target_langs_manual: ['fr_FR'] # languages to manually translate; changed/added lines will be left blank with a comment

# translator_credit_key: 'ui.addon_info:translator_credit' # key to append translator credit to
# translator_credit_value: '§oAuto Translated to {lang} using Google Services§r' # value format for credits
```

Available language codes can be found here. https://py-googletrans.readthedocs.io/en/latest/#googletrans-languages <br>
The script will parse only the language code before the underscore!

Some addons may include a credit section for translators. If yours does, uncomment the last two lines and change the `translator_credit_key`. Any auto translations will be filled with the text in `translator_credit_value`.

## Running the script manually
Setup Environment
```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r .github/scripts/requirements.txt
```

Run
```bash
python .github/scripts/auto_translate.py 
```
