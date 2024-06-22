# Git und SSH-Schlüssel Einrichtung

Um SSH-Schlüssel für GitHub einzurichten, folgen Sie diesen Schritten:

1. **SSH-Schlüssel generieren** (falls noch nicht geschehen):

   - Öffnen Sie ein Terminal.
   - Geben Sie den Befehl `ssh-keygen -t rsa -b 4096 -C "Ihre_Email@example.com"` oder `ssh-keygen -t ed25519 -C "Ihre_Email@example.com"` ein, ersetzen Sie dabei `"Ihre_Email@example.com"` mit Ihrer E-Mail-Adresse, die mit Ihrem GitHub-Konto verknüpft ist.
   - Folgen Sie den Anweisungen, um den Schlüssel zu generieren. Sie können einen Passphrase hinzufügen oder einfach Enter drücken, um keinen zu setzen.

2. **SSH-Schlüssel zum SSH-Agent hinzufügen**:

   - Starten Sie den SSH-Agent im Hintergrund mit dem Befehl `eval "$(ssh-agent -s)"`. Dies startet den SSH-Agenten, der Ihre SSH-Schlüssel verwaltet und im Hintergrund läuft.
   - Wenn Sie einen RSA-Schlüssel generiert haben, verwenden Sie den Befehl ssh-add ~/.ssh/id_rsa.
   - Wenn Sie stattdessen einen ED25519-Schlüssel generiert haben, verwenden Sie den Befehl ssh-add ~/.ssh/id_ed25519.

   Um den generierten SSH-Schlüssel zum SSH-Agenten hinzuzufügen, folgen Sie diesen Schritten, die an die Informationen aus Ihrem aktiven Dokument README.md anschließen:

1. **Starten Sie den SSH-Agent im Hintergrund**:
   - Öffnen Sie ein Terminal.
   - Führen Sie den Befehl `eval "$(ssh-agent -s)"` aus. Dies startet den SSH-Agenten, der Ihre SSH-Schlüssel verwaltet und im Hintergrund läuft.

2. **Fügen Sie Ihren SSH-Schlüssel zum SSH-Agent hinzu**:
   - Wenn Sie einen RSA-Schlüssel generiert haben, verwenden Sie den Befehl `ssh-add ~/.ssh/id_rsa`.
   - Wenn Sie stattdessen einen ED25519-Schlüssel generiert haben, verwenden Sie den Befehl `ssh-add ~/.ssh/id_ed25519`.

Durch das Hinzufügen Ihres SSH-Schlüssels zum SSH-Agenten wird sichergestellt, dass Ihr Schlüssel automatisch verwendet wird, wenn Sie eine SSH-Verbindung zu GitHub (oder anderen Diensten, die SSH verwenden) herstellen, ohne dass Sie jedes Mal Ihr Passwort oder Ihren Schlüssel manuell eingeben müssen.

3. **SSH-Schlüssel zu Ihrem GitHub-Konto hinzufügen**:
   - Kopieren Sie Ihren öffentlichen SSH-Schlüssel in die Zwischenablage. Unter Linux können Sie dies mit `xclip -sel clip < ~/.ssh/id_rsa.pub` oder `xclip -sel clip < ~/.ssh/id_rsa.pub` tun. Falls `xclip` nicht installiert ist, können Sie es mit `sudo apt-get install xclip` installieren oder den Inhalt der Datei `~/.ssh/id_rsa.pub` oder `~/.ssh/id_rsa.pub` mit einem Texteditor öffnen und manuell kopieren.
   - Gehen Sie zu GitHub und melden Sie sich an.
   - Klicken Sie auf Ihr Profilbild in der oberen rechten Ecke und wählen Sie „Settings“ (Einstellungen).
   - Wählen Sie im Benutzermenü auf der linken Seite „SSH and GPG keys“.
   - Klicken Sie auf „New SSH key“ oder „Add SSH key“.
   - Fügen Sie im Feld „Title“ einen beschreibenden Namen für Ihren Schlüssel ein.
   - Fügen Sie Ihren Schlüssel in das Feld „Key“ ein.
   - Klicken Sie auf „Add SSH key“.

Nachdem Sie diese Schritte ausgeführt haben, ist Ihr SSH-Schlüssel Ihrem GitHub-Konto hinzugefügt, und Sie können über SSH mit Ihren Repositories kommunizieren.

Um die Verbindung zu GitHub über SSH zu testen, können Sie den folgenden Befehl in Ihrem Terminal ausführen:

```bash
ssh -T git@github.com
```

Dieser Befehl versucht, eine SSH-Verbindung zum GitHub-Server herzustellen. Wenn Ihre SSH-Schlüssel korrekt eingerichtet sind und zu Ihrem GitHub-Konto hinzugefügt wurden, sollten Sie eine Nachricht ähnlich der folgenden sehen:

```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

Ersetzen Sie `username` durch Ihren tatsächlichen GitHub-Benutzernamen. Diese Nachricht bestätigt, dass Ihre SSH-Verbindung erfolgreich eingerichtet wurde. GitHub bietet keinen Shell-Zugriff, daher ist die Meldung, dass kein Shell-Zugriff bereitgestellt wird, normal und erwartet.

