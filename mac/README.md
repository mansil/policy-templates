**IMPORTANTE**: Estes ficheiros estão em desenvolvimento ativo em conjunto com as políticas no Firefox. Para obter a informação da política que correspondem a um lançamento específico, vá para https://github.com/mozilla/policy-templates/releases.

A partir da versão 64 do Firefox e do Firefox ESR 60.4, o Firefox suporta a configuração de ficheiros no macOS.

Uma lista plist de exemplo com todas as opções está disponível aqui:

https://github.com/mozilla/policy-templates/blob/master/mac/org.mozilla.firefox.plist

Se deseja definir opções específicas a partir da linha de comandos, nós também fornecemos atalhos simplificados para qualquer item que esteja integrado no ficheiro plist.

Por exemplo, esta política:
```json
{
  "policies": {
    "Homepage": {
      "URL": "http://example.com/"
    }
  }
}
```
que seria definida no ficheiro plist, tal como isto:
```plist
  <key>Homepage</key>
  <dict>
    <key>URL</key>
    <string>http://example.com</string>
  </dict>
```
Correctly writing the nested value with the `defaults` command can be hard, so you can flatten the keys by separating them with `__`, like this:
```bash
sudo defaults write /Library/Preferences/org.mozilla.firefox Homepage__URL -string "http://example.com"
```
Before any command line policies will work, you need to enable policies like this:
```bash
sudo defaults write /Library/Preferences/org.mozilla.firefox EnterprisePoliciesEnabled -bool TRUE
```
