# Analytics France — publication SSH et retour arrière préparés, non exécutés

Cette procédure accompagne le commit local de la branche **livraison/ga4-france-20261029**, issu directement de **360d7811c690940dc1fa67ed22f5f2f0873758c3**. Aucun push, SSH, déploiement ou envoi Google n'a été effectué pendant sa préparation. Toute exécution distante ci-dessous nécessite une autorisation ultérieure. La collecte doit rester désactivée, y compris après retour arrière.

## Provenance et rattachement

**Relevé SSH rapporté par l'utilisateur**, non inspecté directement : u664242226@147.93.93.52, port 65002 ; racine Symfony /home/u664242226/domains/francetuncq.fr/public_html ; origin https://github.com/ftuncq/sym-appointment.git ; main à 360d7811c690940dc1fa67ed22f5f2f0873758c3. Seule différence suivie : fin de ligne ajoutée à composer.json. Fichiers non suivis à préserver : .htaccess, public/.htaccess, public/robots.txt, error_log, images public/images/about/ et public/images/avatars/. .env.local privé présent. Ces observations complètent, sans effacer, la réserve historique du dossier de livraison sur l'état déployé inconnu lors de la préparation précédente.

Le commit ajoute les **18 sources exactes** de l'archive adaptée, les sources de tests Analytics et la documentation. Aucun changement fonctionnel supplémentaire, de dépendance ou de composer.json. Les tests et documents ne sont pas des fichiers à exposer comme racine web. Les assets construits sont ignorés par les conventions du dépôt : **aucun ajout forcé** de public/assets ou assets/vendor.

Les neuf fichiers de tests proviennent inchangés du dépôt principal ; AnalyticsTest.php et real_driver.py figuraient aussi dans les sources de revue du candidat. Les sept autres complètent le harnais existant, hors payload applicatif. Leurs empreintes figurent dans le rattachement Git. Les scripts de recette réelle restent à déclenchement explicite et ne sont pas exécutés ici. Seule la nouvelle procédure est vérifiée : syntaxe Bash/PowerShell et six blocs PHP, puis lecture Symfony du désactivateur sur deux répertoires synthétiques, avec et sans cache .env.local.php. Les autres valeurs synthétiques sont préservées ; les permissions Unix et le PHP web réel restent à confirmer sur l'hébergement.

Contrôle Git : les 41 chemins prévus sont seuls indexés. Les octets des tests et des manifestes historiques, dont certains sont en CRLF, sont préservés ; core.autocrlf=false est la configuration existante. Le contrôle d'espaces tenant compte de CRLF signale uniquement une ligne vide finale préexistante dans analytics-ga4-controle-rapports.md, conservée avec le document historique. Les 18 sources applicatives et les deux nouveaux documents passent le contrôle ciblé. Aucune normalisation du candidat ni reconstruction d'assets supplémentaire.

Artefact associé : **20261029-france.zip**, SHA-256 **6e3bb812ffb307c422659f7974a51058ea1c90cdc489238077b397beb31006f3**. C'est un lot, pas une application complète. Ses **86 fichiers public/assets** doivent accompagner les sources du commit ; ne pas reconstruire les assets sur le serveur. Les 18 sources viennent de Git, pas d'une copie aveugle du ZIP. Le manifeste original et [le rattachement Git](analytics-ga4-france-git-20261029.json) identifient les octets sources/assets ; la fiche locale release-sha.txt, créée après le commit, fournit son SHA sans référence circulaire dans le commit.

Les vérifications antérieures portent sur ces mêmes octets : 34 YAML, 55 Twig, 81 assets + cinq métadonnées, trois tests PHP / 49 assertions et cinq pages désactivées contrôlées hors ligne. Pas de nouvelle campagne Analytics pour cette préparation Git. Approbation des mentions par délégation, réception et critère technique de retrait acceptés inchangés. **« Personnalité juridique » du DPA reste ouverte**, à traiter par France/l'administrateur Analytics ; aucune activation autorisée.

## Prérequis précis avant exécution distante

- Confirmer le binaire PHP CLI **compatible avec PHP du site web**, ses extensions et l'état du vendor installé. Le verrou n'a pas changé : aucun composer install/update ni script d'installation n'est requis par ce lot. Arrêter si les dépendances installées ne correspondent pas au verrou.
- Confirmer que PHP web lit la configuration Symfony standard de ce dépôt, et que les variables du panneau hébergeur/PHP-FPM/Apache ne forcent pas GA4_ENABLED à 1/true. Les définir durablement à 0 si elles existent, **avant** de mettre le code Analytics à disposition. Une variable dans le terminal ne suffit pas. Vérifier également APP_ENV=prod / APP_DEBUG=0 effectifs pour le site.
- Confirmer l'identité d'exécution PHP web et les droits de lecture : les fichiers privés seront en mode 600. Les commandes ci-dessous supposent que PHP web s'exécute sous u664242226 et lit ces fichiers. Sinon, déterminer le groupe/droit minimal avec l'hébergeur avant intervention, sans élargissement public des droits.
- Identifier auprès de l'hébergeur le moyen de renouveler PHP/OPcache si sa configuration ne revalide pas les fichiers, et l'éventuel cache HTTP. Aucun service systemd, sudo, script de maintenance, symlink de release ou purge CDN n'est supposé. Ce point reste nécessaire pour garantir que le site sert la nouvelle version.
- Vérifier les droits GitHub permettant la publication dans ftuncq/sym-appointment, la disponibilité serveur de Bash, Git, PHP, curl, unzip, sha256sum et GNU tar, et l'espace disponible pour sauvegarde et extraction. La procédure s'arrête si une condition manque.

La mise à jour proposée est **en place**, conformément à la seule arborescence observée : elle n'est pas atomique entre fichiers Git, assets et cache et ne garantit pas une absence d'interruption. Choisir un créneau approprié avec l'exploitant ; ne pas inventer un dispositif de maintenance. Si une publication atomique est exigée, faire préciser d'abord l'architecture et le docroot autorisés par l'hébergeur. Aucun changement de réservation, paiement, courriel ou base de données ne fait partie de ces commandes.

## 1. Publication Git ultérieure, depuis le poste local

Après autorisation distincte de push/publication seulement, depuis PowerShell. Le remote local **france**, pas origin du dépôt principal, est utilisé. Aucun merge global du projet principal.

~~~powershell
Set-Location C:/Formations/appointment-sym/var/analytics-git/france-20261029
$Release = (Get-Content ../release-sha.txt -Raw).Trim()
if ($Release -notmatch '^[0-9a-f]{40}$') { throw 'SHA invalide' }
if ((git rev-parse HEAD) -ne $Release) { throw 'Branche locale modifiée depuis la préparation' }
if (git status --porcelain) { throw 'Worktree non propre' }
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
ssh -p 65002 u664242226@147.93.93.52 'umask 077; test ! -e /home/u664242226/private-deployments/ga4-20261029 && mkdir -p /home/u664242226/private-deployments/ga4-20261029'
if ($LASTEXITCODE) { throw 'Répertoire de préparation non créé' }
scp -P 65002 C:/Formations/appointment-sym/var/analytics-delivery/20261029-france.zip C:/Formations/appointment-sym/var/analytics-git/release-sha.txt u664242226@147.93.93.52:/home/u664242226/private-deployments/ga4-20261029/
if ($LASTEXITCODE) { throw 'Transfert échoué' }
ssh -p 65002 u664242226@147.93.93.52
~~~

Dans la session SSH, ouvrir **bash**, puis exécuter les étapes successivement, contrôler chaque résultat et s'arrêter à la première divergence. Ne pas copier les blocs de retour arrière pendant la publication.

~~~bash
bash
set -euo pipefail
umask 077
APP=/home/u664242226/domains/francetuncq.fr/public_html
STAGE=/home/u664242226/private-deployments/ga4-20261029
BACKUP="$STAGE/backup"
BASE=360d7811c690940dc1fa67ed22f5f2f0873758c3
RELEASE=$(tr -d '\r\n' < "$STAGE/release-sha.txt")
[[ "$RELEASE" =~ ^[0-9a-f]{40}$ ]]
for tool in git php curl unzip sha256sum tar; do command -v "$tool" >/dev/null; done
php -v
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
php <<'PHP'
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
test "$(git rev-parse "$RELEASE^")" = "$BASE"
test "$(git rev-parse "$BASE:composer.json")" = "$(git rev-parse "$RELEASE:composer.json")"
test "$(git rev-parse "$BASE:composer.lock")" = "$(git rev-parse "$RELEASE:composer.lock")"
printf '%s  %s\n' 6e3bb812ffb307c422659f7974a51058ea1c90cdc489238077b397beb31006f3 "$STAGE/20261029-france.zip" | sha256sum -c -
mkdir -m 700 "$STAGE/extracted"
unzip -q "$STAGE/20261029-france.zip" -d "$STAGE/extracted"
export APP STAGE BACKUP BASE RELEASE
~~~

Examiner les fichiers non suivis rapportés par git status : en cas d'ajout inattendu ou de collision avec un chemin livré, arrêter et rapprocher, sans suppression. Ne pas afficher error_log (qui peut contenir des données). Vérifier le paquet et les dépendances installées par lecture seulement :

~~~bash
php <<'PHP'
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
test ! -L public/assets || { echo 'Assets liés : adapter avant publication'; exit 1; }
if test -d public/assets; then tar -czpf "$BACKUP/assets.tgz" public/assets; fi
chmod 600 "$BACKUP"/*
tar -tzf "$BACKUP/replaced.tgz" >/dev/null
tar -tzf "$BACKUP/private-env.tgz" >/dev/null
tar -tzf "$BACKUP/local-untracked.tgz" >/dev/null
if test -f "$BACKUP/assets.tgz"; then tar -tzf "$BACKUP/assets.tgz" >/dev/null; fi
~~~

Ne pas restaurer en masse les images ou journaux après une publication : ils peuvent avoir évolué depuis la sauvegarde. La sauvegarde des fichiers locaux est une protection supplémentaire ; les opérations Git ci-dessous les laissent en place. La différence de fin de ligne de composer.json reste également sur le serveur : aucun stash, checkout de ce fichier ni réinitialisation.

## 4. Désactivation persistante puis mise à jour

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
php "$STAGE/disable-ga4.php"
# Supprimer seulement la variable du processus de contrôle pour ne pas masquer les fichiers.
env -u GA4_ENABLED APP_ENV=prod APP_DEBUG=0 php <<'PHP'
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
git merge --ff-only "$RELEASE"
test "$(git rev-parse HEAD)" = "$RELEASE"
cmp composer.json "$BACKUP/composer.json"
mkdir -p public/assets
cp -a "$STAGE/extracted/payload/public/assets/." public/assets/
php <<'PHP'
<?php
$m = json_decode(file_get_contents(getenv('STAGE').'/extracted/manifest.json'), true, 512, JSON_THROW_ON_ERROR);
foreach ($m['payload_files'] as $entry) {
    $path = substr($entry['path'], strlen('payload/'));
    if (!is_file($path) || hash_file('sha256', $path) !== $entry['sha256']) {
        fwrite(STDERR, "Source/asset installé différent : ".$path."\n"); exit(1);
    }
}
echo "18 sources et 86 fichiers AssetMapper installés conformes.\n";
PHP
APP_ENV=prod APP_DEBUG=0 php bin/console lint:twig templates
APP_ENV=prod APP_DEBUG=0 php bin/console cache:clear --env=prod --no-debug --no-warmup
APP_ENV=prod APP_DEBUG=0 php bin/console cache:warmup --env=prod --no-debug
git status --short --untracked-files=all
~~~

Les assets hachés antérieurs sont conservés ; les cinq métadonnées AssetMapper sont remplacées ensemble. Les permissions issues de la préparation restrictive supposent le même utilisateur PHP web, confirmé préalablement. Ne pas copier vendor, sources/, support/, evidence/ ou les caches synthétiques depuis le ZIP vers le site. Pas de compilation ni de migration serveur. Réaliser maintenant le renouvellement PHP/OPcache identifié avec l'hébergeur, s'il est nécessaire ; aucune commande universelle n'est inventée ici.

## 5. Contrôle HTTP du site web désactivé

Les commandes curl font seulement des GET HTML, sans exécuter JavaScript ni envoyer d'événements Analytics. Elles ne prouvent pas à elles seules l'absence de toute requête navigateur : la vérification de configuration **réellement servie** complète les preuves navigateur locales du candidat. Ne pas accepter le consentement ni effectuer de réservation.

~~~bash
curl --fail --silent --show-error https://francetuncq.fr/ -o "$BACKUP/after-home.html"
curl --fail --silent --show-error https://francetuncq.fr/politique-de-confidentialite -o "$BACKUP/after-privacy.html"
php <<'PHP'
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
CSS=$(php -r '$m=json_decode(file_get_contents("public/assets/manifest.json"),true,512,JSON_THROW_ON_ERROR); echo $m["styles/app.css"];')
[[ "$CSS" == /assets/* && "$CSS" != *..* ]]
curl --fail --silent --show-error -D "$BACKUP/css-headers.txt" "https://francetuncq.fr$CSS" -o "$BACKUP/served.css"
cmp "public$CSS" "$BACKUP/served.css"
grep -i '^content-type:' "$BACKUP/css-headers.txt"
~~~

Si HTML/configuration/assets ne correspondent pas, ne pas déclarer la publication réussie. Diagnostiquer le cache/OPcache identifié ou revenir en arrière. Aucun test de réception Google n'est nécessaire pour cette publication désactivée. Toute activation, même avec l'ID de production G-MWZX1GYXZE, exige une autorisation distincte.

## 6. Retour arrière précis, sans réécriture de l'historique

Rouvrir Bash et redéfinir APP, STAGE, BACKUP, BASE, RELEASE comme à l'étape 2 si la session a été fermée. Les sauvegardes privées doivent être disponibles. Le retour immédiat utilise un **checkout détaché au socle précédent** : main reste pointée sur le commit publié. Cela ne supprime ni commit ni fichiers locaux non suivis. Consigner cet état ; une correction/reversion publiée ultérieurement sur main relèvera d'une nouvelle intervention autorisée. Ne pas lancer ensuite un pull aveugle qui remettrait le lot retiré.

~~~bash
cd "$APP"
test "$(git rev-parse HEAD)" = "$RELEASE"
git diff --cached --quiet
test -z "$(git diff --name-only -- . ':!composer.json')"
cmp composer.json "$BACKUP/composer.json"
# Si ces contrôles échouent : sauvegarder/rapprocher les nouveaux changements, ne pas forcer.
for file in .env.local .env.local.php .env.prod .env.prod.local; do
    test ! -L "$file"
    if test -f "$file"; then printf '%s\n' "$file"; fi
done > "$STAGE/env-current.list"
cmp "$STAGE/env-current.list" "$BACKUP/env-after.list"
sha256sum -c "$BACKUP/env-after.sha256"
php "$STAGE/disable-ga4.php"
git switch --detach "$BASE"
test "$(git rev-parse HEAD)" = "$BASE"
cmp composer.json "$BACKUP/composer.json"
# Restaurer les anciens assets, sans supprimer les nouveaux fichiers hachés.
if test -f "$BACKUP/assets.tgz"; then tar -xzpf "$BACKUP/assets.tgz" -C "$APP"; fi
mkdir -m 700 "$BACKUP/metadata-retirees"
for file in manifest.json importmap.json entrypoint.app.json entrypoint.analytics.json entrypoint.analytics-frame.json; do
    if ! grep -Fxq "$file" "$BACKUP/asset-metadata-present.list" && test -f "public/assets/$file"; then
        mv -- "public/assets/$file" "$BACKUP/metadata-retirees/$file"
    fi
done
# Configuration : restaurer les autres valeurs, puis maintenir impérativement GA4_ENABLED=0.
# Vérifier d'abord qu'aucun administrateur n'a changé la configuration depuis la publication.
tar -xzpf "$BACKUP/private-env.tgz" -C "$APP"
php "$STAGE/disable-ga4.php"
APP_ENV=prod APP_DEBUG=0 php bin/console cache:clear --env=prod --no-debug --no-warmup
APP_ENV=prod APP_DEBUG=0 php bin/console cache:warmup --env=prod --no-debug
git status --short --untracked-files=all
curl --fail --silent --show-error https://francetuncq.fr/ -o "$BACKUP/rollback-home.html"
curl --fail --silent --show-error https://francetuncq.fr/politique-de-confidentialite -o "$BACKUP/rollback-privacy.html"
~~~

Renouveler PHP/OPcache selon le moyen confirmé et vérifier que la version précédente est servie, sans balise Analytics. Le socle antérieur n'a pas de data-analytics-config : ne pas lui appliquer l'assertion HTML de la nouvelle version. .env.prod.local, créé si nécessaire pour désactiver, reste volontairement avec GA4_ENABLED=0 ; le rollback ne rétablit jamais une valeur activante. Les archives conservent les originaux. Si d'autres valeurs privées ont changé depuis la publication, rapprocher ces changements avant restauration pour ne pas les perdre.

Aucune restauration globale des fichiers non suivis, aucune suppression globale d'assets, aucun git reset --hard, git clean, migration ou retour arrière de base. La désactivation serveur ne constitue pas un ordre instantané aux onglets déjà ouverts : les limites acceptées du retrait et des documents existants restent inchangées.
