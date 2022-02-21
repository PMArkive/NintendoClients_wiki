## [[NEX Protocols]] > [Data Store](Data-Store-Protocol) > Pokemon Bank (115)

This page describes the methods that are only seen in Pokemon Bank.

| Method ID | Method Name |
| --- | --- |
| 40 | [PrepareUploadPokemon](#40-prepareuploadpokemon) |
| 41 | [UploadPokemon](#41-uploadpokemon) |
| 42 | [SearchPokemon](#42-searchpokemon) |
| 43 | [PrepareTradePokemon](#43-preparetradepokemon) |
| 44 | [TradePokemon](#44-tradepokemon) |
| 45 | [DownloadOtherPokemon](#45-downloadotherpokemon) |
| 46 | [DownloadMyPokemon](#46-downloadmypokemon) |
| 47 | [DeletePokemon](#47-deletepokemon) |
| 48 | [GetTransactionParam](#48-gettransactionparam) |
| 49 | [PreparePostBankObject](#49-preparepostbankobject) |
| 50 | [CompletePostBankObject](#50-completepostbankobject) |
| 51 | [PrepareGetBankObject](#51-preparegetbankobject) |
| 52 | [PrepareUpdateBankObject](#52-prepareupdatebankobject) |
| 53 | [CompleteUpdateBankObject](#53-completeupdatebankobject) |
| 54 | [RollbackBankObject](#54-rollbackbankobject) |
| 55 | [GetUnlockKey](#55-getunlockkey) |
| 56 | [RequestMigration](#56-requestmigration) |
| 57 | [GetMigrationStatus](#57-getmigrationstatus) |

# (40) PrepareUploadPokemon
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [GlobalTradeStationRecordKey] | pRecordKey |

# (41) UploadPokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationUploadPokemonParam] | param |

## Response
This method does not return anything.

# (42) SearchPokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationSearchPokemonParam] | param |

## Response
| Type | Name |
| --- | --- |
| [GlobalTradeStationSearchPokemonResult] | pResult |

# (43) PrepareTradePokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationPrepareTradePokemonParam] | param |

## Response
| Type | Name |
| --- | --- |
| [GlobalTradeStationPrepareTradePokemonResult] | pResult |

# (44) TradePokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationTradePokemonParam] | param |

## Response
| Type | Name |
| --- | --- |
| [GlobalTradeStationTradePokemonResult] | pResult |

# (45) DownloadOtherPokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationDownloadOtherPokemonParam] | param |

## Response
| Type | Name |
| --- | --- |
| [GlobalTradeStationTradePokemonResult] | pResult |

# (46) DownloadMyPokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationDownloadMyPokemonParam] | param |

## Response
| Type | Name |
| --- | --- |
| [GlobalTradeStationDownloadMyPokemonResult] | pResult |

# (47) DeletePokemon
## Request
| Type | Name |
| --- | --- |
| [GlobalTradeStationDeletePokemonParam] | param |

## Response
This method does not return anything.

# (48) GetTransactionParam
## Request
| Type | Name |
| --- | --- |
| Uint16 | slotId |

## Response
| Type | Name |
| --- | --- |
| [BankTransactionParam] | pTransactionParam |
| Uint32 | pStatus |
| Uint16 | pApplicationId |

# (49) PreparePostBankObject
## Request
| Type | Name |
| --- | --- |
| Uint16 | slotId |
| Uint32 | size |

## Response
| Type | Name |
| --- | --- |
| [DataStoreReqPostInfo] | pReqPostInfo |

# (50) CompletePostBankObject
## Request
| Type | Name |
| --- | --- |
| [DataStoreCompletePostParam] | param |

## Response
This method does not return anything.

# (51) PrepareGetBankObject
## Request
| Type | Name |
| --- | --- |
| Uint16 | slotId |
| Uint16 | applicationId |

## Response
| Type | Name |
| --- | --- |
| [BankTransactionParam] | pTransactionParam |
| [DataStoreReqGetInfo] | pReqGetInfo |

# (52) PrepareUpdateBankObject
## Request
| Type | Name |
| --- | --- |
| [BankTransactionParam] | transactionParam |

## Response
| Type | Name |
| --- | --- |
| [BankTransactionParam] | pTransactionParam |
| [DataStoreReqUpdateInfo] | pReqUpdateInfo |

# (53) CompleteUpdateBankObject
## Request
| Type | Name |
| --- | --- |
| Uint16 | slotId |
| [BankTransactionParam] | transactionParam |
| Bool | isForce |

## Response
This method does not return anything.

# (54) RollbackBankObject
## Request
| Type | Name |
| --- | --- |
| Uint16 | slotId |
| [BankTransactionParam] | transactionParam |
| Bool | isForce |

## Response
This method does not return anything.

# (55) GetUnlockKey
## Request
| Type | Name |
| --- | --- |
| Uint32 | challengeValue |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;Uint32&gt; | pUnlockKeyList |

# (56) RequestMigration
## Request
| Type | Name |
| --- | --- |
| [String] | oneTimePassword |
| [List]&lt;Uint32&gt; | boxes |

## Response
| Type | Name |
| --- | --- |
| Uint32 | detailCode |

# (57) GetMigrationStatus
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [BankMigrationInfo] | pInfo |
| Uint32 | detailCode |

# Types
## GlobalTradeStationRecordKey ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint64 | password |

## GlobalTradeStationUploadPokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationRecordKey] | prepareUploadKey |
| Uint16 | period |
| [qBuffer] | indexData |
| [qBuffer] | pokemonData |
| [qBuffer] | signature |

## GlobalTradeStationSearchPokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationRecordKey] | prepareUploadKey |
| [List]&lt;Uint32&gt; | conditions |
| Uint8 | resultOrderColumn |
| Uint8 | resultOrder |
| [DateTime] | uploadedAfter |
| [DateTime] | uploadedBefore |
| [ResultRange](NEX-Common-Types#resultrange-structure) | resultRange |

## GlobalTradeStationSearchPokemonResult ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | totalCount |
| [List]&lt;[GlobalTradeStationData]&gt; | result |
| Uint8 | totalCountType |

## GlobalTradeStationTradePokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationTradeKey] | tradeKey |
| [GlobalTradeStationRecordKey] | prepareTradeKey |
| [GlobalTradeStationRecordKey] | prepareUploadKey |
| Uint16 | period |
| [qBuffer] | indexData |
| [qBuffer] | pokemonData |
| [qBuffer] | signature |
| Bool | needData |

## GlobalTradeStationDownloadOtherPokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationRecordKey] | prepareUploadKey |

## GlobalTradeStationDownloadMyPokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationRecordKey] | prepareUploadKey |

## GlobalTradeStationTradePokemonResult ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationDownloadPokemonResult] | result |
| Uint64 | myDataId |

## GlobalTradeStationDownloadMyPokemonResult ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationDownloadPokemonResult] | result |
| Bool | isTraded |

## GlobalTradeStationPrepareTradePokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationTradeKey] | tradeKey |
| [GlobalTradeStationRecordKey] | prepareUploadKey |

## GlobalTradeStationPrepareTradePokemonResult ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationDownloadPokemonResult] | result |
| [GlobalTradeStationRecordKey] | prepareTradeKey |

## GlobalTradeStationDeletePokemonParam ([Structure])
| Type | Name |
| --- | --- |
| [GlobalTradeStationRecordKey] | prepareUploadKey |
| Uint8 | deleteFlag |

## BankTransactionParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | curVersion |
| Uint32 | updateVersion |
| Uint32 | size |
| Uint64 | transactionPassword |

## BankMigrationInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | migrationStatus |
| [DateTime] | updatedTime |

## GlobalTradeStationTradeKey ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | version |

## GlobalTradeStationData ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | ownerId |
| [DateTime] | updatedTime |
| [qBuffer] | indexData |
| Uint32 | version |

## GlobalTradeStationDownloadPokemonResult ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| [qBuffer] | indexData |
| [qBuffer] | pokemonData |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[StationURL]: NEX-Common-Types#stationurl
[Variant]: NEX-Common-Types#variant

[DataStorePrepareGetParamV1]: Data-Store-Protocol#datastorepreparegetparamv1-structure
[DataStoreReqGetInfo]: Data-Store-Protocol#datastorereqgetinfo-structure
[DataStorePreparePostParamV1]: Data-Store-Protocol#datastorepreparepostparamv1-structure
[DataStoreReqPostInfoV1]: Data-Store-Protocol#datastorereqpostinfov1-structure
[DataStoreCompletePostParamV1]: Data-Store-Protocol#datastorecompletepostparamv1-structure
[DataStoreDeleteParam]: Data-Store-Protocol#datastoredeleteparam-structure
[DataStoreChangeMetaParamV1]: Data-Store-Protocol#datastorechangemetaparamv1-structure
[DataStoreGetMetaParam]: Data-Store-Protocol#datastoregetmetaparam-structure
[DataStoreMetaInfo]: Data-Store-Protocol#datastoremetainfo-structure
[DataStorePrepareUpdateParam]: Data-Store-Protocol#datastoreprepareupdateparam-structure
[DataStoreReqUpdateInfo]: Data-Store-Protocol#datastorerequpdateinfo-structure
[DataStoreCompleteUpdateParam]: Data-Store-Protocol#datastorecompleteupdateparam-structure
[DataStoreSearchParam]: Data-Store-Protocol#datastoresearchparam-structure
[DataStoreSearchResult]: Data-Store-Protocol#datastoresearchresult-structure
[DataStoreGetNotificationUrlParam]: Data-Store-Protocol#datastoregetnotificationurlparam-structure
[DataStoreReqGetNotificationUrlInfo]: Data-Store-Protocol#datastorereqgetnotificationurlinfo-structure
[DataStoreGetNewArrivedNotificationsParam]: Data-Store-Protocol#datastoregetnewarrivednotificationsparam-structure
[DataStoreNotificationV1]: Data-Store-Protocol#datastorenotificationv1-structure
[DataStoreRatingTarget]: Data-Store-Protocol#datastoreratingtarget-structure
[DataStoreRateObjectParam]: Data-Store-Protocol#datastorerateobjectparam-structure
[DataStoreRatingInfo]: Data-Store-Protocol#datastoreratinginfo-structure
[DataStoreRatingInfoWithSlot]: Data-Store-Protocol#datastoreratinginfowithslot-structure
[DataStoreGetSpecificMetaParamV1]: Data-Store-Protocol#datastoregetspecificmetaparamv1-structure
[DataStoreSpecificMetaInfoV1]: Data-Store-Protocol#datastorespecificmetainfov1-structure
[DataStorePreparePostParam]: Data-Store-Protocol#datastorepreparepostparam-structure
[DataStoreTouchObjectParam]: Data-Store-Protocol#datastoretouchobjectparam-structure
[DataStoreRatingLog]: Data-Store-Protocol#datastoreratinglog-structure
[DataStoreReqPostInfo]: Data-Store-Protocol#datastorereqpostinfo-structure
[DataStorePrepareGetParam]: Data-Store-Protocol#datastorepreparegetparam-structure
[DataStoreCompletePostParam]: Data-Store-Protocol#datastorecompletepostparam-structure
[DataStoreNotification]: Data-Store-Protocol#datastorenotification-structure
[DataStoreGetSpecificMetaParam]: Data-Store-Protocol#datastoregetspecificmetaparam-structure
[DataStoreSpecificMetaInfo]: Data-Store-Protocol#datastorespecificmetainfo-structure
[DataStorePersistenceInfo]: Data-Store-Protocol#datastorepersistenceinfo-structure
[DataStoreReqGetAdditionalMeta]: Data-Store-Protocol#datastorereqgetadditionalmeta-structure
[DataStorePasswordInfo]: Data-Store-Protocol#datastorepasswordinfo-structure
[DataStoreChangeMetaParam]: Data-Store-Protocol#datastorechangemetaparam-structure

[GlobalTradeStationRecordKey]: #globaltradestationrecordkey-structure
[GlobalTradeStationUploadPokemonParam]: #globaltradestationuploadpokemonparam-structure
[GlobalTradeStationSearchPokemonParam]: #globaltradestationsearchpokemonparam-structure
[GlobalTradeStationSearchPokemonResult]: #globaltradestationsearchpokemonresult-structure
[GlobalTradeStationPrepareTradePokemonParam]: #globaltradestationpreparetradepokemonparam-structure
[GlobalTradeStationPrepareTradePokemonResult]: #globaltradestationpreparetradepokemonresult-structure
[GlobalTradeStationTradePokemonParam]: #globaltradestationtradepokemonparam-structure
[GlobalTradeStationTradePokemonResult]: #globaltradestationtradepokemonresult-structure
[GlobalTradeStationDownloadOtherPokemonParam]: #globaltradestationdownloadotherpokemonparam-structure
[GlobalTradeStationDownloadMyPokemonParam]: #globaltradestationdownloadmypokemonparam-structure
[GlobalTradeStationDownloadMyPokemonResult]: #globaltradestationdownloadmypokemonresult-structure
[GlobalTradeStationDeletePokemonParam]: #globaltradestationdeletepokemonparam-structure
[BankTransactionParam]: #banktransactionparam-structure
[BankMigrationInfo]: #bankmigrationinfo-structure

[DataStorePersistenceTarget]: Data-Store-Protocol#datastorepersistencetarget-structure
[DataStoreKeyValue]: Data-Store-Protocol#datastorekeyvalue-structure
[DataStorePermission]: Data-Store-Protocol#datastorepermission-structure
[DataStoreRatingInitParamWithSlot]: Data-Store-Protocol#datastoreratinginitparamwithslot-structure
[DataStorePersistenceInitParam]: Data-Store-Protocol#datastorepersistenceinitparam-structure
[DataStoreChangeMetaCompareParam]: Data-Store-Protocol#datastorechangemetacompareparam-structure

[GlobalTradeStationData]: #globaltradestationdata-structure
[GlobalTradeStationTradeKey]: #globaltradestationtradekey-structure
[GlobalTradeStationDownloadPokemonResult]: #globaltradestationdownloadpokemonresult-structure
[DataStoreRatingInitParam]: #datastoreratinginitparam-structure