# Build status

Este projeto contém um app iOS em Swift/Objective-C (`ThreeOneOSFive.xcodeproj`) e um painel PHP em `Admin_Client/`.

## iOS

A compilação do app requer macOS com Xcode e o SDK iOS 16+. O projeto fornecido não contém um scheme compartilhado; o target configurado é `3105`. O workflow [`ios-build.yml`](.github/workflows/ios-build.yml) tenta gerar um build **sem assinatura** para o iOS Simulator em cada push. Para gerar um IPA instalável, é necessário configurar uma equipe de desenvolvimento/certificados Apple e executar o archive/export no Xcode ou em um runner macOS com esses segredos.

Comando equivalente no macOS:

```bash
xcodebuild -project ThreeOneOSFive.xcodeproj \
  -target 3105 \
  -sdk iphonesimulator \
  -configuration Debug \
  -destination 'generic/platform=iOS Simulator' \
  CODE_SIGNING_ALLOWED=NO CODE_SIGNING_REQUIRED=NO build
```

## Painel PHP

O painel requer PHP 8+, `pdo_mysql` e MySQL/MariaDB. Não versionar `database.config.php`, credenciais ou logs de servidor. Use `database.config.example.php` como modelo.
