# Minecraft Warfare — pack packwiz

Pack de mods client du serveur **Minecraft Warfare**, distribue avec
[packwiz](https://packwiz.infra.link/).

| | |
|---|---|
| Minecraft | 1.20.1 |
| Forge | 47.4.10 (exactement la version du serveur) |
| TaCZ | 1.1.8-hotfix2 (epinglee) |
| warfare | 0.4.0 (le mod du serveur, fichier local) |
| Optimisation | Embeddium, FerriteCore, ModernFix |

Pas de shaders : Oculus provoque des crashs documentes avec les armes TaCZ
(tickets MCModderAnchor/TACZ #250 et Asek3/Oculus #678).

## Pour les joueurs

Ne telecharge pas ce depot a la main : suis `docs/AMIS.md` du projet.
L'instance Prism Launcher met le pack a jour toute seule a chaque lancement.

## Pour mettre le pack a jour (cote admin)

Depuis le dossier du projet principal :

```bash
# Mettre a jour un mod depuis Modrinth
./tools/packwiz update embeddium
./tools/packwiz update --all

# Apres avoir recompile le mod warfare
rm pack/mods/warfare-*.jar
cp mod/build/libs/warfare-<version>.jar pack/mods/
(cd pack && ../tools/packwiz refresh)

# Puis publier
cd pack && git add -A && git commit -m "pack: warfare <version>" && git push
```

`packwiz refresh` est **obligatoire** apres tout ajout ou suppression de fichier :
c'est lui qui recalcule `index.toml`, et c'est l'index que lisent les clients.
