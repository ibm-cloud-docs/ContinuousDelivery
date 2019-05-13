---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-26"

keywords: Git source control, personal access token, Git repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Lokale Clients für die Git-Quellcodeverwaltung einrichten
{: #git_local}


Sie können Ihren Quellcode in einem GitHub-, GitHub Enterprise- oder {{site.data.keyword.gitrepos}}-Repository verwalten und damit arbeiten (lokal oder in der {{site.data.keyword.webide}} von Eclipse Orion). Wenn Sie lokal arbeiten möchten, klonen Sie Ihr Repository mit einem Git-Client (z. B. mit der Git-Befehlszeilenschnittstelle) und bearbeiten Sie den Code mit Ihrem bevorzugten Editor. Wenn Sie in Eclipse arbeiten, können Sie das EGit-Plug-in für die Versionssteuerung installieren.

## Git-Projekt über die Befehlszeile klonen


## Vorbemerkungen
{: #git_before_clone}

1. Um außerhalb des Browsers auf den Git-Server zuzugreifen, müssen Sie möglicherweise ein persönliches Zugriffstoken oder einen SSH-Schlüssel für die Authentifizierung erstellen. Die folgende Tabelle zeigt, was Sie tun müssen, um die Authentifizierung einzurichten.

| Git-Typ  | HTTPS-Setup | HTTPS-Verwendung |  SSH-Setup |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking  | [Persönliches Zugriffstoken](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) | Git Repos and Issue Tracking-Benutzername (nicht Ihre IBMid) und persönliches Zugriffstoken | [SSH-Schlüssel konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#creating-an-ssh-key) |
| Öffentlicher GitHub (github.com) | Kein persönliches Zugriffstoken erforderlich, aber Sie können eines einrichten und verwenden | GitHub-Benutzername und Kennwort oder GitHub-Benutzername und persönliches Zugriffstoken oder nur persönliches Zugriffstoken als Benutzername | [GitHub-SSH-Schlüssel konfigurieren](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Persönliches Zugriffstoken](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) | GitHub Enterprise-Benutzername (nicht Ihre IBMid) und persönliches Zugriffstoken | [GitHub Enterprise-SSH-Schlüssel konfigurieren](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) |

Wenn Sie lieber SSH verwenden möchten, können Sie einen einzigen Schlüssel für alle Git-Server verwenden. Erstellen oder suchen Sie Ihren Schlüssel und konfigurieren Sie ihn für jeden Server, wie dies in den vorherigen Links beschrieben ist. Wenn Sie Ihren Schlüssel mit einer Kennphrase erstellen, werden Sie zur Eingabe dieser Kennphrase aufgefordert, wenn Sie den Schlüssel verwenden.
{: tip}

2. Führen Sie bei Verwendung der Git-Befehlszeile die folgenden Schritte aus:

    a. Überprüfen Sie, ob Git installiert ist. Geben Sie in einer Befehlszeile `git version` ein. Wenn Git installiert ist, wird die Versionsnummer angezeigt und Sie können beginnen.

    b. Wenn Git nicht nicht installiert ist, [rufen Sie die Git-Website auf ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://git-scm.com/downloads){: new_window}.

    c. Laden Sie die Version für Ihr Betriebssystem herunter und installieren Sie sie. Sie können die Standardinstallationswerte übernehmen.


### Projekt klonen
{: #git_clone}

Sie können eine lokale Kopie der Projektdateien erstellen, indem Sie das Git-Repository klonen, sodass Sie auf den Inhalt Ihres Repositorys von außerhalb der Web-IDE mit einem Desktop-Tool zugreifen können.

1. Klicken Sie auf der Übersichtsseite Ihrer Toolchain auf die Karte für das Repository, das Sie klonen möchten.

2. Stellen Sie Ihre Repository-URL zusammen:

   a. Klicken Sie in GitHub auf **Klonen oder herunterladen**. Wenn Sie HTTPS verwenden möchten, wählen Sie **HTTPS verwenden** aus.  Wenn Sie SSH verwenden möchten, klicken Sie auf **SSH verwenden**. Klicken Sie auf das Symbol für die Zwischenablage, um die URL zu kopieren.

   b. Wählen Sie in Git Repos and Issue Tracking entweder **HTTPS** oder **SSH** aus und kopieren Sie die URL in das Feld.

3. Öffnen Sie eine Befehlszeile.

4. Ändern Sie das Verzeichnis in die Position, an der die lokale Kopie des Git-Repositorys gespeichert werden soll.

5. Geben Sie `git clone` ein, fügen Sie die URL ein und drücken Sie die Eingabetaste.

6. Wenn Sie zur Authentifizierung aufgefordert werden, geben Sie die entsprechenden Informationen ein (wie in der vorherigen Tabelle definiert).


Wenn der Download abgeschlossen ist, haben Sie eine lokale Version der Dateien in Ihrem Repository. Weitere Informationen zur Verwendung von Git finden Sie in der [Git-Dokumentation ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")]](http://git-scm.com/doc){: new_window}.


## Mit Eclipse und dem EGit-Plug-in auf das Repository zugreifen
{: #git_egit}

Wenn Sie Eclipse verwenden und ein Projekt haben, das Git für die Quellcodeverwaltung verwendet, können Sie das EGit-Plug-in verwenden, um Ihre Repositorys von Eclipse aus zu verwalten. Weitere Informationen zur Installation und Konfiguration von EGit finden Sie im [EGit-Lernprogramm ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.

Wenn Sie bei der Verwendung von {{site.data.keyword.gitrepos}} auf Probleme stoßen, finden Sie weitere Informationen in der [{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_local)-Dokumentation. 
