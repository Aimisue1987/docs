---
title: Solucionar problemas de tu codespace
intro: Use this guide to help you troubleshoot common issues with your codespace.
redirect_from:
  - /github/developing-online-with-github-codespaces/troubleshooting-your-codespace
  - /github/developing-online-with-codespaces/troubleshooting-your-codespace
  - /codespaces/working-with-your-codespace/troubleshooting-your-codespace
versions:
  free-pro-team: '*'
type: reference
topics:
  - Codespaces
---

{% data reusables.codespaces.release-stage %}

### Known Limitations

{% data reusables.codespaces.beta-functionality-limited %}

{% data reusables.codespaces.unsupported-repos %}

### {% data variables.product.prodname_vscode %} troubleshooting

Use **Issues** in the [`microsoft/vscode`](https://github.com/microsoft/vscode/issues) repository to check for known issues or to log issues about the {% data variables.product.prodname_vscode %} experience.


### Configuration troubleshooting

{% data reusables.codespaces.recovery-mode %}

```
Este codespace se ejecuta acutalmente en modo de recuperación debido a un error del contenedor.
```

Review the creation logs, update the configuration as needed, and run **Codespaces: Rebuild Container** in the command palette to retry. Para obtener más información, consulta la sección "[Configurar {% data variables.product.prodname_codespaces %} para tu proyecto](/github/developing-online-with-codespaces/configuring-codespaces-for-your-project#apply-changes-to-your-configuration)".

### dotfiles troubleshooting

- Make sure your dotfiles repository is public. If you have secrets or sensitive data you want to use in your codespace, use [Codespace secrets](/codespaces/managing-your-codespaces/managing-encrypted-secrets-for-your-codespaces) instead of private dotfiles.
- Check `/workspaces/.codespaces/.persistedshare/dotfiles` to see if your dotfiles were cloned.
  - If your dotfiles were cloned, try manually re-running your install script to verify it's executable.
  - If your dotfiles weren't cloned, check `/workspaces/.codespaces/.persistedshare/EnvironmentLog.txt` to see if there was a problem cloning them.
- Check `/workspaces/.codespaces/.persistedshare/creation.log` for possible issues. Alternatively, you can view the `creation.log` by navigating to the command palette and entering **Codespaces: View Creation Log**.


### Browser troubleshooting

Si encuentras problemas al utilizar un buscador que no se base en Chromium, intenta cambiar a uno que sí se base en él, o revisa los problemas conocidos de tu buscador en el repositorio `microsoft/vscode` buscando los problemas etiquetados con el nombre del buscador, tales como [`firefox`](https://github.com/microsoft/vscode/issues?q=is%3Aissue+is%3Aopen+label%3Afirefox) o [`safari`](https://github.com/Microsoft/vscode/issues?q=is%3Aopen+is%3Aissue+label%3Asafari).

Si encuentras problemas al utilizar un buscador basado en Chromium, puedes revisar si estás experimentando otro problema conocido con {% data variables.product.prodname_vscode %} en el repositorio [`microsoft/vscode`](https://github.com/microsoft/vscode/issues).

### Container storage troubleshooting

When you create a codespace, it has a finite amount of storage and over time it may be necessary for you to free up space. Try any of the following items to free up storage space.

- Remove packages that are no longer by using `sudo apt autoremove`
- Clean the apt cache by using `sudo apt clean`
- Delete unneeded files like build artifacts and logs (these are very project-dependent)
- See the top 10 largest files in the codespace: `sudo find / -printf '%s %p\n'| sort -nr | head -10`

More destructive options:
- Remove unused Docker images, networks, and containers by using `docker system prune` (append `-a` if you want to remove all images, and `--volumes` if you want to remove all volumes)
- Remove untracked files from working tree: `git clean -i`

### Contáctanos

Si aún necesitas ayuda, puedes contactarnos. Para obtener más información, consulta la sección "[Acerca de {% data variables.product.prodname_codespaces %}](/github/developing-online-with-codespaces/about-codespaces#contacting-us-about-codespaces)".
