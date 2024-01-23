# PalSave

> Easy move you save in steam(windows) to linux dedicated server

## Project struct

```text
PalSave
├── savefiles
├── fix-host-save.sav
├── README.md
└── uesave.exe
```

## Precheck

> [!IMPORTANT]
> Give the guild president to any other members

## What we have now?

- in `windows`
  - ~/AppData/Local/Pal/Saved/SaveGames/`<STEAM_ID>`

    ```text
    .
    └── <SAVE_DIR>
        ├── LevelMeta.sav
        ├── Level.sav
        ├── LocalData.sav
        └── Players
            ├── 00000000000000000000000000000001.sav
            └── ... // other players' save if exists

    ```


- in `linux server`
  - `...`/Pal/Saved/SaveGames/`0`

    ```text
    .
    └── <SERVER_SAVE_DIR>
        ├── LevelMeta.sav
        ├── Level.sav
        └── Players
            └── <SERVER_SAVE_FILENAME>.sav
    ```

1. Copy files in `<SAVE_DIR>` to `<SERVER_SAVE_DIR>` (override if exists)
2. Restart server
3. Connect to server and you can see the `world` has been replaced.
4. Copy `<SERVER_SAVE_FILENAME>.sav` to `PalSave/savefiles/Players/`
5. In `PalSave`, run

    ```bash
    python ./fix-host-save.py ./uesave.exe ./savefiles <SERVER_SAVE_FILENAME>
    ```

    and the save `00000000000000000000000000000001.sav` will replace the old `<SERVER_SAVE_FILENAME>.sav`

6. After finish, copy `PalSave/saverfiles/<SERVER_SAVE_FILENAME>` to `SERVER_SAVE_DIR/` (override the old save)
