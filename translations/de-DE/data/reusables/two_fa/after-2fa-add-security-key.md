Nachdem Du 2FA mit einer mobilen App{% if currentVersion == "free-pro-team@latest" %} oder per SMS{% endif %} konfiguriert hast, kannst Du einen Sicherheitsschlüssel hinzufügen, zum Beispiel einen Fingerabdruckleser oder Windows Hello. {% if currentVersion == "free-pro-team@latest" or currentVersion ver_gt "enterprise-server@2.18" %}Die Technologie, welche die Authentifizierung mit einem Sicherheitsschlüssel ermöglicht, heißt WebAuthn. WebAuthn ist der Nachfolger von U2F und arbeitet in allen modernen Browsern. Weitere Informationen findest du unter „[WebAuthn](https://webauthn.guide/)" und „[Can I Use](https://caniuse.com/#search=webauthn)" (Kann ich es verwenden).{% else %}FIDO U2F Authentifizierung ist momentan verfügbar für die Browser Chrome, Firefox und Opera.{% endif %}