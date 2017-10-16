---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Upgrade für vertrauliche IBM Projekte auf Toolchains durchführen 
{: #upgrade_public_or_cio}

Aus {{site.data.keyword.jazzhub}} wird künftig IBM Bluemix {{site.data.keyword.contdelivery_short}}. Als Teil dieser Änderungen wird für Projekte ein Upgrade auf Toolchains durchgeführt.

Wenn Ihr Projekt bereit für das Upgrade ist, wird eine Nachricht auf seiner Übersichtsseite angezeigt. Dann können Sie für das Projekt das Upgrade auf eine Toolchain auf {{site.data.keyword.Bluemix_notm}} Public durchführen. Die Toolchain wird ein Whitewater {{site.data.keyword.ghe_short}}-Repository (repo) für Ihren Quellcode enthalten. Whitewater {{site.data.keyword.ghe_short}} wird IBM Teams bereitgestellt, um Social Coding innerhalb von IBM zu ermöglichen und zu fördern. 
{: shortdesc}

**{{site.data.keyword.contdelivery_short}}-Toolchains werden für vertrauliches IBM Material genehmigt, wenn die Verwendung in Verbindung mit Whitewater {{site.data.keyword.ghe_short}} erfolgt.** Delivery Pipelines, die ihre Eingabe über Whitewater {{site.data.keyword.ghe_short}}-Repositorys erhalten, können in Staging-Umgebungen (YS1) und öffentlichen Umgebungen (YP) bereitgestellt werden.

Während des Upgradeprozesses werden Sie aufgefordert, {{site.data.keyword.contdelivery_short}} die Zugriffsgenehmigung auf Whitewater {{site.data.keyword.ghe_short}} in Ihrem Namen zu erteilen.

## Nach erfolgtem Upgrade Mitglieder zum Whitewater {{site.data.keyword.ghe_short}}-Repository hinzufügen

Wenn Ihr Projekt ein Repository verwendet, das unter JazzHub gehostet wird, so wird beim Upgrade ein neues Repository unter Whitewater {{site.data.keyword.ghe_short}} erstellt. Nach Abschluss des Upgradeprozesses muss die Person, von der das Upgrade gestartet wurde, Teammitglieder zum Whitewater {{site.data.keyword.ghe_short}}-Repository hinzufügen und sicherstellen, dass die Mitglieder jeweils die ordnungsgemäßen Berechtigungen erhalten, um auf das neue Repository zugreifen zu können.

## Fehlerbehebung

Bei dem Versuch, das Ziel einer Pipeline-Entwicklungsstage ändern, kann sporadisch vorübergehend ein Problem auftreten. Trifft dies zu, wird in den Feldern **Organisation** und **Bereich** ein Fehler angezeigt.

Dieses Problem tritt normalerweise nur dann auf, wenn Sie das Ziel der Pipeline ändern, sodass die Pipeline, die während des Upgradeprozesses erstellt wird, ordnungsgemäß auf denselben Zielen wie zuvor bereitgestellt wird.

Wenn Sie versuchen, das Ziel zu ändern, und im Zuge dieser Änderung dieses Problem auftritt, wechseln Sie einige Male zwischen den Zielen hin und her, bis die Felder **Organisation** und **Bereich** belegt sind.

Ein verwandtes Problem bewirkt gelegentlich, dass die Bereitstellung auf YS1-Zielen fehlschlägt. Dieser Fall ist selten, doch sollte falls er eintritt, führen Sie die Pipeline erneut aus.

Das IBM DevOps Services-Team arbeitet aktiv an der Behebung dieser Probleme.
