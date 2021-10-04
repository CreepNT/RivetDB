# Databases for the [Rivet](https://github.com/CreepNT/Rivet) bot
`rivetdb.json` contains a hexadecimal -> facility + name + description mapping

`short_codes.json` contains a short code -> hexadecimal mapping

# Contributing to the error codes database
To have a coherent database, you must follow certain guidelines when contributing to the database.
When submitting a Pull Request, indicate which error code names and/or descriptions, if any, are official names/descriptions.
Official names will always be kept as-is, while official descriptions may have to be reworked.

Non-official error codes should respect the following rules:
* Names always begins with `SCE_xxx_ERROR_`
    * Replace `xxx` with either:
        * Facility name if clearly identified (i.e. `RUDP`)
        * Sub-facility name for multi-purpose facilities (i.e.`VSH` or `CODEC` facilities)
        * Module name, in capital letters, with extension and leading `Sce` stripped if necessary (i.e. `lib_dyld.suprx` -> `LIB_DYLD`)
* Rest of the name is a **short** description of the error
    * Non-trivial errors can have a longer name, but try to keep it as short as possible
    * You can also provide no name, and just a description of the error.
    In such cases, set the `"name"` key to `Unknown error name (0xXXXX)` where `XXXX` is the low 16-bits of the error code
        * (0x80020004 -> `Unknown error name (0x0004)`)
* Description of the error must:
    * Be a passive voice sentense
        * ❌ `You provided an incorrect UID`
        * ✅ `The UID provided is incorrect`
    * Start with the subject or its adjective(s)
        * ❌ `The UID provided is incorrect`
        * ✅ `Incorrect UID has been provided`
    * Leave out unnecessary words and grammatical constructs
        * ❌ `Incorrect UID has been provided`
        * ✅ `Incorrect UID provided`
    * ***Try*** *to be consistent with the Sony descriptions*
        * Check the KERNEL facility errors for reference
* Description can contain additional information
    * Separate the error description and additional information with a ` - `
        * Example: `Not allowed to call this routine - generally a IsSceShell/IsRootApp/IsSIEApp check failure`

Please check for grammatical and syntaxic errors - typos will not be allowed.
An cleanup of the existing codes to respect those rules as much as possible is ongoing.

# Contributing to the short error codes database
When submitting your Pull Request, please indicate where the error codes mapping came from.