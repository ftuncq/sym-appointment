# Analytics France — publication SSH et retour arrière préparés, non exécutés

## Actualisation — production du 30 octobre 2026

**Déploiement, activation autorisée puis exécutée et réception des quatre événements dans Temps réel confirmés par l’utilisateur.** Voir le [compte rendu de mise en production](analytics-ga4-production-20261030.md). Les opérations et captures sont rapportées par l’utilisateur et son assistant ; aucune inspection directe du serveur, d’Analytics ou des captures de production par cet agent.

La procédure ci-dessous décrit la préparation initialement désactivée et la récupération. Son titre et ses restrictions historiques ne signifient plus qu’aucun déploiement n’a eu lieu : la publication du commit 29bcd686bc1dc5e7dfdccbfb937cead80c19c6bc puis l’activation sur G-MWZX1GYXZE sont rapportées exécutées. PHP web 8.4.27 / UID 664242226 et OPcache activé / validate_timestamps=1 / revalidate_freq=2 sont désormais confirmés par l’utilisateur. Les commandes ne sont pas rejouées, et le rapport n’atteste pas leur transcription exacte sur le serveur.

Les statuts de préparation et de recette qui suivent sont conservés comme **historique daté**, sans annuler les acquis du 30 octobre ni rouvrir les contrôles déjà confirmés. Aucune nouvelle opération serveur n’est autorisée par cette actualisation.

## Historique conservé

Cette procédure, corrigée le **30 octobre 2026**, accompagne la branche **livraison/ga4-france-20261029**. Le commit applicatif **7033249c538127371ef23f4e25670edd547c83df** reste intact, directement issu du socle **360d7811c690940dc1fa67ed22f5f2f0873758c3**. Un commit documentaire supplémentaire porte cette correction ; le SHA à livrer est celui de release-sha.txt, et son parent direct n’est donc plus le socle. Aucun push, SSH, déploiement ou envoi Google n'a été effectué pendant sa préparation. Toute exécution distante ci-dessous nécessite une autorisation ultérieure. La collecte doit rester désactivée, y compris après retour arrière.

## Provenance et rattachement

**Relevé SSH rapporté par l'utilisateur**, non inspecté directement : u664242226@147.93.93.52, port 65002 ; racine Symfony /home/u664242226/domains/francetuncq.fr/public_html ; origin https://github.com/ftuncq/sym-appointment.git ; main à 360d7811c690940dc1fa67ed22f5f2f0873758c3. Seule différence suivie : fin de ligne ajoutée à composer.json. Fichiers non suivis à préserver : .htaccess, public/.htaccess, public/robots.txt, error_log, images public/images/about/ et public/images/avatars/. .env.local privé présent. Ces observations complètent, sans effacer, la réserve historique du dossier de livraison sur l'état déployé inconnu lors de la préparation précédente.

Le commit applicatif du 29 octobre ajoute les **18 sources exactes** de l'archive adaptée, les sources de tests Analytics et la documentation. Aucun changement fonctionnel supplémentaire, de dépendance ou de composer.json. Les tests et documents ne sont pas des fichiers à exposer comme racine web. Les assets construits sont ignorés par les conventions du dépôt : **aucun ajout forcé** de public/assets ou assets/vendor.

**Historique du 29 octobre :** les neuf fichiers de tests proviennent inchangés du dépôt principal ; AnalyticsTest.php et real_driver.py figuraient aussi dans les sources de revue du candidat. Les sept autres complètent le harnais existant, hors payload applicatif. Leurs empreintes figurent dans le rattachement Git. Les scripts de recette réelle restent à déclenchement explicite et ne sont pas exécutés ici. Seule la nouvelle procédure est vérifiée : syntaxe Bash/PowerShell et six blocs PHP, puis lecture Symfony du désactivateur sur deux répertoires synthétiques, avec et sans cache .env.local.php. Les autres valeurs synthétiques sont préservées ; les permissions Unix et le PHP web réel restent à confirmer sur l'hébergement.

**Contrôle Git historique du 29 octobre :** les 41 chemins prévus étaient seuls indexés. Les octets des tests et des manifestes historiques, dont certains sont en CRLF, sont préservés ; core.autocrlf=false est la configuration existante. Le contrôle d'espaces tenant compte de CRLF signale uniquement une ligne vide finale préexistante dans analytics-ga4-controle-rapports.md, conservée avec le document historique. Les 18 sources applicatives et les deux nouveaux documents passent le contrôle ciblé. Aucune normalisation du candidat ni reconstruction d'assets supplémentaire.

Artefact associé : **20261029-france.zip**, SHA-256 **6e3bb812ffb307c422659f7974a51058ea1c90cdc489238077b397beb31006f3**. C'est un lot, pas une application complète. Ses **86 fichiers public/assets** doivent accompagner les sources du commit ; ne pas reconstruire les assets sur le serveur. Les 18 sources viennent de Git, pas d'une copie aveugle du ZIP. Le manifeste original et [le rattachement Git](analytics-ga4-france-git-20261029.json) identifient les octets sources/assets ; la fiche locale release-sha.txt, créée après le commit, fournit son SHA sans référence circulaire dans le commit.

Les vérifications antérieures portent sur ces mêmes octets : 34 YAML, 55 Twig, 81 assets + cinq métadonnées, trois tests PHP / 49 assertions et cinq pages désactivées contrôlées hors ligne. Pas de nouvelle campagne Analytics pour cette préparation Git. Approbation des mentions par délégation, réception et critère technique de retrait acceptés inchangés. **« Personnalité juridique » du DPA reste ouverte**, à traiter par France/l'administrateur Analytics ; aucune activation autorisée.

## Vérifications documentaires du 30 octobre 2026

Seuls cette procédure et son rattachement JSON sont modifiés. Le commit applicatif et le ZIP restent inchangés. Syntaxe Bash, PowerShell et blocs PHP vérifiée ; huit scénarios de récupération ont été exécutés dans des dépôts Git jetables avec Git Bash et PHP local 8.4.27 : aucun début de mutation ; configuration partielle sans inventaire après modification ; Git avancé ; assets partiellement copiés ; échec du cache ; échec du cache pendant la récupération puis reprise ; absence d’assets initiaux ; modification suivie inattendue (arrêt préservant cette modification). Le contrôle d’ascendance fonctionne avec un commit documentaire après le commit applicatif. Aucune recette Analytics rejouée.

Les fixtures utilisent uniquement des fichiers synthétiques et un substitut de commande cache, pas une application en ligne. Les appels install -m 644 / chmod 755 sont contrôlés pour leur portée ; les octets restaurés et les fichiers locaux préservés sont vérifiés. **Limite :** Git Bash sur NTFS ne démontre pas les permissions POSIX effectives ni les droits du processus web. Aucun Linux/WSL n’est installé sur ce poste. Les contrôles de mode ajoutés ci-dessous doivent donc aussi réussir sur l’hébergement avant de déclarer l’installation terminée. Un ajustement du harnais tar (--force-local pour les lettres de lecteur Windows) n’affecte pas les commandes Linux documentées. Preuves locales : var/analytics-git/procedure-check-20261030/results.json.

## Complément serveur rapporté le 30 octobre 2026

Selon l’utilisateur : PHP web sélectionné dans Hostinger **8.4** ; /usr/bin/php **8.3.36** ; binaire CLI confirmé **/opt/alt/php84/usr/bin/php**, version **8.4.27**. Dossiers publics 755, public/index.php 644 ; .env.local 644, propriétaire u664242226, groupe o1006897413. **Le propriétaire du fichier ne démontre pas l’identité du processus PHP web**, qui reste à vérifier. HEAD et différences locales sont rapportés inchangés. Aucune inspection SSH directe dans cette correction.

## Prérequis précis avant exécution distante

- Vérifier à nouveau le binaire CLI 8.4 confirmé et ses extensions, puis l'état du vendor installé. Le verrou n'a pas changé : aucun composer install/update ni script d'installation n'est requis par ce lot. Arrêter si les dépendances installées ne correspondent pas au verrou.
- Confirmer que PHP web lit la configuration Symfony standard de ce dépôt, et que les variables du panneau hébergeur/PHP-FPM/Apache ne forcent pas GA4_ENABLED à 1/true. Les définir durablement à 0 si elles existent, **avant** de mettre le code Analytics à disposition. Une variable dans le terminal ne suffit pas. Vérifier également APP_ENV=prod / APP_DEBUG=0 effectifs pour le site.
- **Avant toute modification de configuration**, confirmer l’identité effective et les groupes du processus PHP web pour ce site, et sa capacité à lire les futurs fichiers privés en 600. Le mode 644 observé ne prouve pas qu’un passage à 600 est utilisable. Si PHP web n’a pas les droits nécessaires, faire définir par Hostinger un groupe/une ACL minimale et adapter le plan avant de continuer. Ne pas déduire cette identité du propriétaire de .env.local, de l’utilisateur SSH, de PHP CLI ou de get_current_user(). Les dossiers/fichiers des assets publics livrés sont, eux, explicitement fixés à 755/644.
- Identifier auprès de l'hébergeur le moyen de renouveler PHP/OPcache si sa configuration ne revalide pas les fichiers, et l'éventuel cache HTTP. Aucun service systemd, sudo, script de maintenance, symlink de release ou purge CDN n'est supposé. Ce point reste nécessaire pour garantir que le site sert la nouvelle version.
- Vérifier les droits GitHub permettant la publication dans ftuncq/sym-appointment, la disponibilité serveur de Bash, Git, du binaire PHP_BIN, curl, unzip, sha256sum, install et GNU tar, et l'espace disponible pour sauvegarde et extraction. La procédure s'arrête si une condition manque.

Commandes minimales de lecture, à exécuter uniquement lors d’une intervention SSH autorisée ; elles ne montrent ni valeurs d’environnement ni contenu privé :

~~~bash
PHP_BIN=/opt/alt/php84/usr/bin/php
test -x "$PHP_BIN"
"$PHP_BIN" -v
"$PHP_BIN" --ini
"$PHP_BIN" -m
stat -c '%a %u %g %U %G %n' /home/u664242226/domains/francetuncq.fr/public_html/public /home/u664242226/domains/francetuncq.fr/public_html/public/index.php /home/u664242226/domains/francetuncq.fr/public_html/.env.local
ps -eo pid,euid,egid,comm | awk 'NR == 1 || $4 ~ /^(lsphp|php-fpm)/'
~~~

La liste des processus n’affiche pas leurs arguments. Elle peut être masquée ou montrer plusieurs pools : elle ne suffit alors pas à rattacher un UID au domaine. Demander ce rattachement à Hostinger, ainsi que les groupes/ACL applicables. Confirmer dans le panneau/support Hostinger les variables **web** GA4_ENABLED=0 ou absente, APP_ENV=prod, APP_DEBUG=0, les réglages OPcache et le moyen de renouveler PHP si nécessaire. Les sorties CLI ne prouvent pas les réglages web ; aucun phpinfo public ou dump d’environnement n’est demandé.

La mise à jour proposée est **en place**, conformément à la seule arborescence observée : elle n'est pas atomique entre fichiers Git, assets et cache et ne garantit pas une absence d'interruption. Choisir un créneau approprié avec l'exploitant ; ne pas inventer un dispositif de maintenance. Si une publication atomique est exigée, faire préciser d'abord l'architecture et le docroot autorisés par l'hébergeur. Aucun changement de réservation, paiement, courriel ou base de données ne fait partie de ces commandes.

## 1. Publication Git ultérieure, depuis le poste local

Après autorisation distincte de push/publication seulement, depuis PowerShell. Le remote local **france**, pas origin du dépôt principal, est utilisé. Aucun merge global du projet principal.

~~~powershell
Set-Location C:/Formations/appointment-sym/var/analytics-git/france-20261029
$Release = (Get-Content ../release-sha.txt -Raw).Trim()
if ($Release -notmatch '^[0-9a-f]{40}$') { throw 'SHA invalide' }
if ((git rev-parse HEAD) -ne $Release) { throw 'Branche locale modifiée depuis la préparation' }
if (git status --porcelain) { throw 'Worktree non propre' }
git merge-base --is-ancestor 7033249c538127371ef23f4e25670edd547c83df $Release
if ($LASTEXITCODE) { throw 'Commit applicatif absent de la livraison' }
if (git diff --name-only 7033249c538127371ef23f4e25670edd547c83df $Release -- . ':!docs/analytics-ga4-publication-ssh.md' ':!docs/analytics-ga4-france-git-20261029.json') { throw 'Différence hors correction documentaire' }
if ((git remote get-url france) -ne 'https://github.com/ftuncq/sym-appointment.git') { throw 'Mauvais remote' }
git fetch france main
if ($LASTEXITCODE) { throw 'Fetch échoué' }
if ((git rev-parse france/main) -ne '360d7811c690940dc1fa67ed22f5f2f0873758c3') { throw 'main distant a évolué : rapprocher avant publication' }
git push france "${Release}:refs/heads/livraison/ga4-france-20261029"
if ($LASTEXITCODE) { throw 'Push de branche échoué' }
# Publication de main également soumise à autorisation : fast-forward, sans force.
git push france "${Release}:refs/heads/main"
if ($LASTEXITCODE) { throw 'Publication de main échouée : ne pas forcer' }
~~~

Si la protection de main exige une PR/revue, suivre cette règle dans une intervention autorisée et conserver **le même commit par fast-forward**. Si la politique impose squash/rebase ou un merge, le SHA change : identifier et vérifier ce nouveau commit, actualiser le rattachement et les instructions avant déploiement. Ne pas contourner la protection ni déployer un SHA supposé.

## 2. Transfert et précontrôle SSH, après autorisation

Depuis PowerShell, créer un répertoire privé neuf **hors racine web** et transférer les seuls artefacts identifiés. Le refus si le répertoire existe évite de réutiliser une sauvegarde : choisir un nouveau nom partout si nécessaire, ne rien écraser.

~~~powershell
ssh -p 65002 u664242226@147.93.93.52 'umask 077; test ! -e /home/u664242226/private-deployments/ga4-20261030 && mkdir -p /home/u664242226/private-deployments/ga4-20261030'
if ($LASTEXITCODE) { throw 'Répertoire de préparation non créé' }
scp -P 65002 C:/Formations/appointment-sym/var/analytics-delivery/20261029-france.zip C:/Formations/appointment-sym/var/analytics-git/release-sha.txt u664242226@147.93.93.52:/home/u664242226/private-deployments/ga4-20261030/
if ($LASTEXITCODE) { throw 'Transfert échoué' }
ssh -p 65002 u664242226@147.93.93.52
~~~

Dans la session SSH, ouvrir **bash**, puis exécuter les étapes successivement, contrôler chaque résultat et s'arrêter à la première divergence. Ne pas copier les blocs de retour arrière pendant la publication.

~~~bash
bash
set -euo pipefail
umask 077
APP=/home/u664242226/domains/francetuncq.fr/public_html
STAGE=/home/u664242226/private-deployments/ga4-20261030
BACKUP="$STAGE/backup"
BASE=360d7811c690940dc1fa67ed22f5f2f0873758c3
APP_COMMIT=7033249c538127371ef23f4e25670edd547c83df
PHP_BIN=/opt/alt/php84/usr/bin/php
RELEASE=$(tr -d '\r\n' < "$STAGE/release-sha.txt")
[[ "$RELEASE" =~ ^[0-9a-f]{40}$ ]]
test -x "$PHP_BIN"
for tool in git curl unzip sha256sum tar install; do command -v "$tool" >/dev/null; done
"$PHP_BIN" -v
df -h "$APP" "$STAGE"
cd "$APP"
test "$(git rev-parse --show-toplevel)" = "$APP"
test "$(git remote get-url origin)" = https://github.com/ftuncq/sym-appointment.git
test "$(git branch --show-current)" = main
test "$(git rev-parse HEAD)" = "$BASE"
git status --short --untracked-files=all
git diff --cached --quiet
# Aucune différence suivie hors composer.json n'est admise.
test -z "$(git diff --name-only -- . ':!composer.json')"
"$PHP_BIN" <<'PHP'
<?php
$base = shell_exec('git show HEAD:composer.json');
$current = file_get_contents('composer.json');
if (!is_string($base) || !in_array($current, [$base, $base."\n", $base."\r\n"], true)) {
    fwrite(STDERR, "composer.json diffère autrement que par une fin de ligne : arrêt.\n"); exit(1);
}
echo "composer.json : inchangé ou seule fin de ligne ajoutée.\n";
PHP
test -f .env.local
test -f vendor/autoload.php
# Ne pas afficher .env.local ni les valeurs de l'environnement.
git fetch origin main
test "$(git rev-parse origin/main)" = "$RELEASE"
test "$(git rev-parse "$APP_COMMIT^")" = "$BASE"
git merge-base --is-ancestor "$BASE" "$RELEASE"
git merge-base --is-ancestor "$APP_COMMIT" "$RELEASE"
test -z "$(git diff --name-only "$APP_COMMIT" "$RELEASE" -- . ':!docs/analytics-ga4-publication-ssh.md' ':!docs/analytics-ga4-france-git-20261029.json')"
test "$(git rev-parse "$BASE:composer.json")" = "$(git rev-parse "$RELEASE:composer.json")"
test "$(git rev-parse "$BASE:composer.lock")" = "$(git rev-parse "$RELEASE:composer.lock")"
printf '%s  %s\n' 6e3bb812ffb307c422659f7974a51058ea1c90cdc489238077b397beb31006f3 "$STAGE/20261029-france.zip" | sha256sum -c -
chmod 700 "$STAGE"
chmod 600 "$STAGE/20261029-france.zip" "$STAGE/release-sha.txt"
mkdir -m 700 "$STAGE/extracted"
unzip -q "$STAGE/20261029-france.zip" -d "$STAGE/extracted"
find "$STAGE/extracted" -type d -exec chmod 700 {} +
find "$STAGE/extracted" -type f -exec chmod 600 {} +
export APP STAGE BACKUP BASE RELEASE APP_COMMIT PHP_BIN
~~~

Examiner les fichiers non suivis rapportés par git status : en cas d'ajout inattendu ou de collision avec un chemin livré, arrêter et rapprocher, sans suppression. Ne pas afficher error_log (qui peut contenir des données). Vérifier le paquet et les dépendances installées par lecture seulement :

~~~bash
"$PHP_BIN" <<'PHP'
<?php
$root = getenv('STAGE').'/extracted';
$manifest = json_decode(file_get_contents($root.'/manifest.json'), true, 512, JSON_THROW_ON_ERROR);
foreach ($manifest['archive_files'] as $entry) {
    $file = $root.'/'.$entry['path'];
    if (!is_file($file) || hash_file('sha256', $file) !== $entry['sha256']) {
        fwrite(STDERR, "Paquet incohérent : ".$entry['path']."\n"); exit(1);
    }
}
$lock = json_decode(file_get_contents('composer.lock'), true, 512, JSON_THROW_ON_ERROR);
$installed = json_decode(file_get_contents('vendor/composer/installed.json'), true, 512, JSON_THROW_ON_ERROR);
$versions = array_column($installed['packages'] ?? $installed, null, 'name');
foreach ($lock['packages'] as $package) {
    $actual = $versions[$package['name']] ?? [];
    if (($actual['version'] ?? null) !== $package['version'] || ($actual['source']['reference'] ?? null) !== ($package['source']['reference'] ?? null)) {
        fwrite(STDERR, "Dépendance à rapprocher : ".$package['name']."\n"); exit(1);
    }
}
echo "Paquet et versions/références des dépendances de production vérifiés.\n";
PHP
~~~

## 3. Sauvegarde restrictive, avant toute modification de fichiers servis

Les sauvegardes contiennent des secrets : mode 700 pour le répertoire, 600 pour les archives, jamais sous public_html ni jointes à Git. Le site n'étant pas mis en maintenance par cette procédure, la copie des fichiers locaux changeants n'est pas un instantané transactionnel : si tar signale une modification pendant la copie, arrêter et refaire une sauvegarde cohérente avant de continuer.

~~~bash
cd "$APP"
mkdir -m 700 "$BACKUP"
git rev-parse HEAD > "$BACKUP/head.txt"
git status --porcelain=v1 --untracked-files=all > "$BACKUP/status.txt"
git diff --binary -- composer.json > "$BACKUP/composer-local.patch"
cp -p composer.json "$BACKUP/composer.json"
git diff --name-only --diff-filter=M "$BASE" "$RELEASE" > "$BACKUP/replaced.list"
git diff --name-only --diff-filter=A "$BASE" "$RELEASE" > "$BACKUP/added.list"
tar -czpf "$BACKUP/replaced.tgz" -T "$BACKUP/replaced.list"
git ls-files --others --exclude-standard -z > "$BACKUP/local-untracked.list0"
tar -czpf "$BACKUP/local-untracked.tgz" --null -T "$BACKUP/local-untracked.list0"
: > "$BACKUP/env-present.list"
for file in .env.local .env.local.php .env.prod .env.prod.local; do
    test ! -L "$file" || { echo 'Configuration liée : adapter la sauvegarde avant de poursuivre'; exit 1; }
    if test -e "$file"; then test -f "$file"; printf '%s\n' "$file" >> "$BACKUP/env-present.list"; fi
done
tar -czpf "$BACKUP/private-env.tgz" -T "$BACKUP/env-present.list"
: > "$BACKUP/asset-metadata-present.list"
for file in manifest.json importmap.json entrypoint.app.json entrypoint.analytics.json entrypoint.analytics-frame.json; do
    if test -f "public/assets/$file"; then printf '%s\n' "$file" >> "$BACKUP/asset-metadata-present.list"; fi
done
test ! -L public
if test -d public/assets; then test -z "$(find public/assets -type l -print -quit)"; fi
test ! -L public/assets || { echo 'Assets liés : adapter avant publication'; exit 1; }
if test -d public/assets; then tar -czpf "$BACKUP/assets.tgz" public/assets; fi
chmod 600 "$BACKUP"/*
tar -tzf "$BACKUP/replaced.tgz" >/dev/null
tar -tzf "$BACKUP/private-env.tgz" >/dev/null
tar -tzf "$BACKUP/local-untracked.tgz" >/dev/null
if test -f "$BACKUP/assets.tgz"; then tar -tzf "$BACKUP/assets.tgz" >/dev/null; fi
# Liste NUL des seuls fichiers publics concernés ; les noms peuvent contenir des espaces.
"$PHP_BIN" <<'PHP' > "$BACKUP/asset-files.list0"
<?php
$m = json_decode(file_get_contents(getenv('STAGE').'/extracted/manifest.json'), true, 512, JSON_THROW_ON_ERROR);
$count = 0;
foreach ($m['payload_files'] as $entry) {
    $path = substr($entry['path'], strlen('payload/'));
    if (!str_starts_with($path, 'public/assets/')) { continue; }
    if (str_contains($path, '..') || str_contains($path, "\0") || str_contains($path, "\\")) { throw new RuntimeException('Chemin non admis'); }
    echo $path, "\0"; ++$count;
}
if ($count !== 86) { throw new RuntimeException('Inventaire assets inattendu'); }
PHP
chmod 600 "$BACKUP/asset-files.list0"
touch "$BACKUP/ready"
~~~

Ne pas restaurer en masse les images ou journaux après une publication : ils peuvent avoir évolué depuis la sauvegarde. La sauvegarde des fichiers locaux est une protection supplémentaire ; les opérations Git ci-dessous les laissent en place. La différence de fin de ligne de composer.json reste également sur le serveur : aucun stash, checkout de ce fichier ni réinitialisation.

## 4. Désactivation persistante puis mise à jour

Les marqueurs sont écrits **avant** chaque mutation et peuvent donc désigner une étape partielle. Ils n’affirment pas sa réussite. Ne jamais poursuivre après une erreur ; utiliser la récupération de la section 6, qui accepte aussi HEAD=BASE. Créer les deux auxiliaires ci-dessous avant de commencer les mutations ; ils sont privés et ne font pas partie de l’application.

~~~bash
cat > "$STAGE/assets-functions.sh" <<'SH'
# Ce fichier est sourcé par Bash ; aucun parcours hors public/assets.
asset_dirs() {
    local rel="$1" rest component cursor="$APP/public"
    [[ "$rel" == public/assets/* && "$rel" != *..* && "$rel" != *\\* ]] || return 1
    test -d "$cursor" && test ! -L "$cursor" || return 1
    rest="${rel%/*}"; rest="${rest#public/}"
    while test -n "$rest"; do
        component="${rest%%/*}"; cursor="$cursor/$component"
        test ! -L "$cursor" || return 1
        if ! test -d "$cursor"; then mkdir -- "$cursor" || return 1; fi
        chmod 755 -- "$cursor" || return 1
        if [[ "$rest" == */* ]]; then rest="${rest#*/}"; else rest=''; fi
    done
    test ! -L "$APP/$rel" || return 1
    if test -e "$APP/$rel"; then test -f "$APP/$rel" || return 1; fi
}
install_assets() {
    local rel
    while IFS= read -r -d '' rel; do
        asset_dirs "$rel" || return 1
        install -m 644 -- "$STAGE/extracted/payload/$rel" "$APP/$rel" || return 1
    done < "$BACKUP/asset-files.list0"
}
restore_assets() {
    local rel old="$BACKUP/old-assets" retired
    mkdir -p -- "$old" "$BACKUP/metadata-retirees" || return 1
    chmod 700 -- "$old" "$BACKUP/metadata-retirees" || return 1
    if test -f "$BACKUP/assets.tgz"; then tar -xzpf "$BACKUP/assets.tgz" -C "$old" || return 1; fi
    find "$old" -type d -exec chmod 700 {} + || return 1
    find "$old" -type f -exec chmod 600 {} + || return 1
    while IFS= read -r -d '' rel; do
        if test -f "$old/$rel"; then
            asset_dirs "$rel" || return 1
            install -m 644 -- "$old/$rel" "$APP/$rel" || return 1
        else
            # Les nouveaux fichiers hachés restent ; seules les nouvelles métadonnées sont retirées.
            case "$rel" in
                public/assets/manifest.json|public/assets/importmap.json|public/assets/entrypoint.app.json|public/assets/entrypoint.analytics.json|public/assets/entrypoint.analytics-frame.json)
                    test ! -L "$APP/$rel" || return 1
                    if test -f "$APP/$rel"; then
                        retired=$(mktemp "$BACKUP/metadata-retirees/metadata-XXXXXX") || return 1
                        mv -- "$APP/$rel" "$retired" || return 1
                        chmod 600 -- "$retired" || return 1
                    fi ;;
            esac
        fi
    done < "$BACKUP/asset-files.list0"
}
SH
chmod 600 "$STAGE/assets-functions.sh"
source "$STAGE/assets-functions.sh"
~~~

**Arrêt obligatoire avant cette étape si les prérequis PHP web / variables d'hébergement / droits ne sont pas confirmés.** Le script ci-dessous, stocké hors racine web, ne révèle aucune valeur privée. Il ajoute uniquement une dernière affectation GA4_ENABLED=0 dans .env.local et .env.prod.local, et met la même valeur dans le cache d'environnement .env.local.php s'il existe. Toutes les autres valeurs, dont une éventuelle destination de production, sont conservées. Les originaux viennent d'être sauvegardés. Aucun ID de recette n'est injecté.

~~~bash
cat > "$STAGE/disable-ga4.php" <<'PHP'
<?php
$root = getenv('APP');
if (!$root || !is_file($root.'/.env.local')) { throw new RuntimeException('Racine/configuration absente'); }
function replacePrivate(string $path, string $content): void {
    if (is_link($path)) { throw new RuntimeException('Lien non admis'); }
    $tmp = tempnam(dirname($path), '.ga4-private-');
    if ($tmp === false) { throw new RuntimeException('Fichier temporaire impossible'); }
    chmod($tmp, 0600);
    if (file_put_contents($tmp, $content, LOCK_EX) !== strlen($content) || !rename($tmp, $path)) {
        throw new RuntimeException('Écriture privée échouée');
    }
}
foreach (['.env.local', '.env.prod.local'] as $name) {
    $path = $root.'/'.$name;
    $text = is_file($path) ? file_get_contents($path) : '';
    if ($text === false) { throw new RuntimeException('Lecture privée échouée'); }
    replacePrivate($path, $text."\n# Livraison Analytics : collecte désactivée\nGA4_ENABLED=0\n");
}
$compiled = $root.'/.env.local.php';
if (is_file($compiled)) {
    $values = require $compiled;
    if (!is_array($values)) { throw new RuntimeException('Cache environnement inattendu'); }
    $values['GA4_ENABLED'] = '0';
    replacePrivate($compiled, "<?php\nreturn ".var_export($values, true).";\n");
}
echo "Configuration persistante désactivée ; aucune valeur privée affichée.\n";
PHP
chmod 600 "$STAGE/disable-ga4.php"
test -f "$BACKUP/ready"
touch "$BACKUP/config-started"
"$PHP_BIN" "$STAGE/disable-ga4.php"
# Supprimer seulement la variable du processus de contrôle pour ne pas masquer les fichiers.
env -u GA4_ENABLED APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" <<'PHP'
<?php
require 'vendor/autoload.php';
(new Symfony\Component\Dotenv\Dotenv())->bootEnv('.env');
if (($_SERVER['GA4_ENABLED'] ?? null) !== '0') { throw new RuntimeException('Désactivation persistante non effective côté CLI'); }
echo "Lecture Symfony prod : GA4_ENABLED=0.\n";
PHP
: > "$BACKUP/env-after.list"
for file in .env.local .env.local.php .env.prod .env.prod.local; do
    if test -f "$file"; then printf '%s\n' "$file" >> "$BACKUP/env-after.list"; fi
done
while IFS= read -r file; do sha256sum -- "$file"; done < "$BACKUP/env-after.list" > "$BACKUP/env-after.sha256"
touch "$BACKUP/config-checked"
touch "$BACKUP/git-started"
git merge --ff-only "$RELEASE"
test "$(git rev-parse HEAD)" = "$RELEASE"
cmp composer.json "$BACKUP/composer.json"
touch "$BACKUP/assets-started"
install_assets
touch "$BACKUP/assets-installed"
"$PHP_BIN" <<'PHP'
<?php
$m = json_decode(file_get_contents(getenv('STAGE').'/extracted/manifest.json'), true, 512, JSON_THROW_ON_ERROR);
foreach ($m['payload_files'] as $entry) {
    $path = substr($entry['path'], strlen('payload/'));
    if (!is_file($path) || hash_file('sha256', $path) !== $entry['sha256']) {
        fwrite(STDERR, "Source/asset installé différent : ".$path."\n"); exit(1);
    }
    if (str_starts_with($path, 'public/assets/')) {
        clearstatcache(true, $path);
        if ((fileperms($path) & 0777) !== 0644) { throw new RuntimeException('Mode fichier public incorrect'); }
        for ($dir = dirname($path); $dir !== 'public'; $dir = dirname($dir)) {
            clearstatcache(true, $dir);
            if ((fileperms($dir) & 0777) !== 0755) { throw new RuntimeException('Mode dossier assets incorrect'); }
        }
    }
}
echo "18 sources et 86 fichiers AssetMapper installés conformes.\n";
PHP
touch "$BACKUP/cache-started"
APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" bin/console lint:twig templates
APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" bin/console cache:clear --env=prod --no-debug --no-warmup
APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" bin/console cache:warmup --env=prod --no-debug
touch "$BACKUP/cache-ready"
git status --short --untracked-files=all
~~~

Les assets hachés antérieurs sont conservés. Les cinq métadonnées font partie de la copie ; celle-ci n’est pas atomique et peut être interrompue. Chaque fichier livré est installé en 644, ses seuls dossiers nécessaires sous public/assets sont fixés à 755. Aucun chmod récursif de public, des images métier ou des autres assets. La préparation et les sauvegardes restent en 700/600, indépendamment des permissions publiques. Les fichiers d’environnement restent soumis au prérequis d’identité PHP web ci-dessus. Ne pas copier vendor, sources/, support/, evidence/ ou les caches synthétiques depuis le ZIP vers le site. Pas de compilation ni de migration serveur. Réaliser maintenant le renouvellement PHP/OPcache identifié avec l'hébergeur, s'il est nécessaire ; aucune commande universelle n'est inventée ici.

## 5. Contrôle HTTP du site web désactivé

Les commandes curl font seulement des GET HTML, sans exécuter JavaScript ni envoyer d'événements Analytics. Elles ne prouvent pas à elles seules l'absence de toute requête navigateur : la vérification de configuration **réellement servie** complète les preuves navigateur locales du candidat. Ne pas accepter le consentement ni effectuer de réservation.

~~~bash
curl --fail --silent --show-error https://francetuncq.fr/ -o "$BACKUP/after-home.html"
curl --fail --silent --show-error https://francetuncq.fr/politique-de-confidentialite -o "$BACKUP/after-privacy.html"
"$PHP_BIN" <<'PHP'
<?php
foreach (['after-home.html', 'after-privacy.html'] as $name) {
    $html = file_get_contents(getenv('BACKUP').'/'.$name);
    if (!preg_match('/data-analytics-config="([^"]+)"/', $html, $match)) { throw new RuntimeException('Configuration servie absente'); }
    $config = json_decode(html_entity_decode($match[1], ENT_QUOTES | ENT_HTML5, 'UTF-8'), true, 512, JSON_THROW_ON_ERROR);
    if ($config['enabled'] !== false || $config['id'] !== '') { throw new RuntimeException('Collecte web non désactivée'); }
    if (preg_match('#<script[^>]+src=["\x27][^"\x27]*googletagmanager#i', $html)) { throw new RuntimeException('Balise inattendue'); }
}
$privacy = file_get_contents(getenv('BACKUP').'/after-privacy.html');
if (!str_contains($privacy, 'France Tuncq et le prestataire chargé du développement et de la maintenance du site')) { throw new RuntimeException('Mentions absentes'); }
echo "Configuration web servie désactivée et mentions présentes.\n";
PHP
~~~

Contrôler aussi que l'URL du CSS haché référencée par le nouveau manifest.json est servie en HTTP 200 avec le bon type MIME et la bonne empreinte (aucune connexion Google) :

~~~bash
CSS=$("$PHP_BIN" -r '$m=json_decode(file_get_contents("public/assets/manifest.json"),true,512,JSON_THROW_ON_ERROR); echo $m["styles/app.css"];')
[[ "$CSS" == /assets/* && "$CSS" != *..* ]]
curl --fail --silent --show-error -D "$BACKUP/css-headers.txt" "https://francetuncq.fr$CSS" -o "$BACKUP/served.css"
cmp "public$CSS" "$BACKUP/served.css"
grep -i '^content-type:' "$BACKUP/css-headers.txt"
~~~

Si HTML/configuration/assets ne correspondent pas, ne pas déclarer la publication réussie. Diagnostiquer le cache/OPcache identifié ou revenir en arrière. Aucun test de réception Google n'est nécessaire pour cette publication désactivée. Toute activation, même avec l'ID de production G-MWZX1GYXZE, exige une autorisation distincte.

## 6. Récupération selon l’étape réellement atteinte

| État observé | Action |
| --- | --- |
| Sauvegarde incomplète, aucun config-started | Aucun fichier servi n’a été modifié par cette procédure : rester au socle et terminer/renouveler la préparation |
| config-started, HEAD=BASE, même sans config-checked/env-after | Réappliquer la désactivation ; ne pas exiger de SHA post-configuration ; conserver main au socle, ne pas toucher aux assets |
| HEAD=RELEASE (ou APP_COMMIT), assets non commencés | Désactiver, revenir au socle détaché, renouveler son cache |
| assets-started, copie complète ou partielle | Même retour Git si nécessaire ; restaurer uniquement les chemins livrés qui existaient avant, retirer les seules nouvelles métadonnées, garder les fichiers hachés supplémentaires |
| cache-started ou échec clear/warmup | Restaurer code/assets puis reconstruire le cache du socle avec PHP_BIN ; si cela échoue encore, conserver cet état, corriger la cause et reprendre la récupération |

Les marqueurs aident à choisir ; **HEAD et l’état des fichiers font foi**. Un checkout Git interrompu avec différences suivies inattendues, un autre HEAD ou des changements simultanés d’un administrateur impose un rapprochement sauvegardé, jamais un reset forcé. Les chemins de récupération ci-dessous ne dépendent pas d’un env-after complet et peuvent être repris quand HEAD est déjà revenu à BASE.

Dans une nouvelle session, définir les variables de récupération directement (ne pas rejouer le précontrôle qui crée STAGE ou exige main/HEAD=BASE) :

~~~bash
bash
set -euo pipefail
umask 077
APP=/home/u664242226/domains/francetuncq.fr/public_html
STAGE=/home/u664242226/private-deployments/ga4-20261030
BACKUP="$STAGE/backup"
BASE=360d7811c690940dc1fa67ed22f5f2f0873758c3
APP_COMMIT=7033249c538127371ef23f4e25670edd547c83df
PHP_BIN=/opt/alt/php84/usr/bin/php
RELEASE=$(tr -d '\r\n' < "$STAGE/release-sha.txt")
[[ "$RELEASE" =~ ^[0-9a-f]{40}$ ]]
export APP STAGE BACKUP BASE RELEASE APP_COMMIT PHP_BIN
test -x "$PHP_BIN"
cd "$APP"
test "$(git rev-parse --show-toplevel)" = "$APP"
test -f "$BACKUP/ready"
test "$(cat "$BACKUP/head.txt")" = "$BASE"
git merge-base --is-ancestor "$APP_COMMIT" "$RELEASE"
CURRENT=$(git rev-parse HEAD)
case "$CURRENT" in "$BASE"|"$APP_COMMIT"|"$RELEASE") ;; *) echo 'HEAD inattendu : rapprocher sans forcer'; exit 1 ;; esac
git diff --cached --quiet
test -z "$(git diff --name-only -- . ':!composer.json')"
cmp composer.json "$BACKUP/composer.json"
~~~

La seule modification de configuration de ce lot est la désactivation : **ne pas extraire private-env.tgz sur les fichiers actifs**, ce qui pourrait réactiver une ancienne valeur et perdre des modifications privées ultérieures. Relancer le désactivateur conserve toutes les autres valeurs présentes et termine aussi une écriture interrompue entre deux fichiers. Les originaux restent dans la sauvegarde restrictive pour rapprochement manuel si une autre réparation est nécessaire. Aucun chmod 644 de .env.local n’est prescrit pour contourner un défaut d’identité/droits PHP.

~~~bash
# BEGIN RECOVERY ACTIONS
if ! test -f "$BACKUP/config-started" && test "$CURRENT" = "$BASE"; then
    echo 'Aucune mutation servie commencée ; pas de retour arrière nécessaire.'
else
    test -f "$STAGE/disable-ga4.php"
    "$PHP_BIN" "$STAGE/disable-ga4.php"
    if test "$CURRENT" != "$BASE"; then git switch --detach "$BASE"; fi
    test "$(git rev-parse HEAD)" = "$BASE"
    cmp composer.json "$BACKUP/composer.json"
    if test -f "$BACKUP/assets-started"; then
        test -f "$STAGE/assets-functions.sh"
        source "$STAGE/assets-functions.sh"
        restore_assets
    fi
    # Contrôle des fichiers persistants, sans variable CLI masquant leur valeur.
    env -u GA4_ENABLED APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" <<'PHP'
<?php
require 'vendor/autoload.php';
(new Symfony\Component\Dotenv\Dotenv())->bootEnv('.env');
if (($_SERVER['GA4_ENABLED'] ?? null) !== '0') { throw new RuntimeException('Désactivation persistante non effective'); }
echo "Configuration prod persistante : désactivée.\n";
PHP
    if ! APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" bin/console cache:clear --env=prod --no-debug --no-warmup; then
        echo 'Code/assets restaurés, cache non rétabli : corriger la cause puis reprendre la section 6.'; exit 1
    fi
    if ! APP_ENV=prod APP_DEBUG=0 "$PHP_BIN" bin/console cache:warmup --env=prod --no-debug; then
        echo 'Code/assets restaurés, warmup échoué : corriger la cause puis reprendre la section 6.'; exit 1
    fi
    touch "$BACKUP/recovery-complete"
fi
# END RECOVERY ACTIONS
git status --short --untracked-files=all
curl --fail --silent --show-error https://francetuncq.fr/ -o "$BACKUP/rollback-home.html"
curl --fail --silent --show-error https://francetuncq.fr/politique-de-confidentialite -o "$BACKUP/rollback-privacy.html"
~~~

Si le désactivateur échoue encore (droits/espace/configuration), arrêter : ne pas poursuivre de publication ni élargir les permissions sans le contrôle web requis. Les écritures individuelles d’environnement sont atomiques, pas l’ensemble des fichiers ; une reprise doit réussir avant de déclarer la configuration rétablie. Si Git a été retiré, main reste pointée sur la livraison et le serveur est détaché au socle : consigner cet état, ne pas faire un pull aveugle qui réinstallerait le lot. Une reversion publiée sur main serait une intervention distincte.

Renouveler PHP/OPcache selon le moyen confirmé et vérifier la version précédente servie. Elle n’a pas de data-analytics-config : ne pas lui appliquer l’assertion HTML du nouveau lot. Si le cache échoue, le fait d’avoir restauré Git ne suffit pas à déclarer le site rétabli. .env.prod.local créé pour la désactivation reste volontairement à 0. Les fichiers locaux et données ne sont pas restaurés en masse ; aucune suppression globale d’assets, migration ou réinitialisation Git. Les limites acceptées concernant les onglets déjà ouverts restent inchangées.
