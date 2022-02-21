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
## DataStorePrepareGetParamV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | dataId |
| Uint32 | lockId |

## DataStorePrepareGetParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | lockId |
| [DataStorePersistenceTarget] | persistenceTarget |
| Uint64 | accessPassword |

## DataStoreReqGetInfo ([Structure])
| Type | Name |
| --- | --- |
| [String] | url |
| [List]&lt;[DataStoreKeyValue]&gt; | requestHeaders |
| Uint32 | size |
| [Buffer] | rootCaCert |

## DataStoreReqGetAdditionalMeta ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | ownerId |
| Uint16 | dataType |
| Uint16 | version |
| [qBuffer] | metaBinary |

## DataStorePreparePostParamV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | size |
| [String] | name |
| Uint16 | dataType |
| [qBuffer] | metaBinary |
| [DataStorePermission] | permission |
| [DataStorePermission] | delPermission |
| Uint32 | flag |
| Uint16 | period |
| Uint32 | referDataId |
| [List]&lt;[String]&gt; | tags |
| [List]&lt;[DataStoreRatingInitParamWithSlot]&gt; | ratingInitParams |

## DataStorePreparePostParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | size |
| [String] | name |
| Uint16 | dataType |
| [qBuffer] | metaBinary |
| [DataStorePermission] | permission |
| [DataStorePermission] | delPermission |
| Uint32 | flag |
| Uint16 | period |
| Uint32 | referDataId |
| [List]&lt;[String]&gt; | tags |
| [List]&lt;[DataStoreRatingInitParamWithSlot]&gt; | ratingInitParams |
| [DataStorePersistenceInitParam] | persistenceInitParam |

## DataStoreReqPostInfoV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | dataId |
| [String] | url |
| [List]&lt;[DataStoreKeyValue]&gt; | requestHeaders |
| [List]&lt;[DataStoreKeyValue]&gt; | formFields |
| [Buffer] | rootCaCert |

## DataStoreReqPostInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| [String] | url |
| [List]&lt;[DataStoreKeyValue]&gt; | requestHeaders |
| [List]&lt;[DataStoreKeyValue]&gt; | formFields |
| [Buffer] | rootCaCert |

## DataStoreCompletePostParamV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | dataId |
| Bool | isSuccess |

## DataStoreCompletePostParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Bool | isSuccess |

## DataStoreDeleteParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint64 | updatePassword |

## DataStoreChangeMetaParamV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | modifiesFlag |
| [String] | name |
| [DataStorePermission] | permission |
| [DataStorePermission] | delPermission |
| Uint16 | period |
| [qBuffer] | metaBinary |
| [List]&lt;[String]&gt; | tags |
| Uint64 | updatePassword |

## DataStoreChangeMetaParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | modifiesFlag |
| [String] | name |
| [DataStorePermission] | permission |
| [DataStorePermission] | delPermission |
| Uint16 | period |
| [qBuffer] | metaBinary |
| [List]&lt;[String]&gt; | tags |
| Uint64 | updatePassword |
| Uint32 | referredCnt |
| Uint16 | dataType |
| Uint8 | status |
| [DataStoreChangeMetaCompareParam] | compareParam |

## DataStoreGetMetaParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| [DataStorePersistenceTarget] | persistenceTarget |
| Uint8 | resultOption |
| Uint64 | accessPassword |

## DataStoreRatingInfo ([Structure])
| Type | Name |
| --- | --- |
| Sint64 | totalValue |
| Uint32 | count |
| Sint64 | initialValue |

## DataStoreRatingInfoWithSlot ([Structure])
| Type | Name |
| --- | --- |
| Sint8 | slot |
| [DataStoreRatingInfo] | rating |

## DataStoreMetaInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | ownerId |
| Uint32 | size |
| [String] | name |
| Uint16 | dataType |
| [qBuffer] | metaBinary |
| [DataStorePermission] | permission |
| [DataStorePermission] | delPermission |
| [DateTime] | createdTime |
| [DateTime] | updatedTime |
| Uint16 | period |
| Uint8 | status |
| Uint32 | referredCnt |
| Uint32 | referDataId |
| Uint32 | flag |
| [DateTime] | referredTime |
| [DateTime] | expireTime |
| [List]&lt;[String]&gt; | tags |
| [List]&lt;[DataStoreRatingInfoWithSlot]&gt; | ratings |

## DataStorePrepareUpdateParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | size |
| Uint64 | updatePassword |

## DataStoreReqUpdateInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | version |
| [String] | url |
| [List]&lt;[DataStoreKeyValue]&gt; | requestHeaders |
| [List]&lt;[DataStoreKeyValue]&gt; | formFields |
| [Buffer] | rootCaCert |

## DataStoreCompleteUpdateParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | version |
| Bool | isSuccess |

## DataStoreSearchParam ([Structure])
| Type | Name |
| --- | --- |
| Uint8 | searchTarget |
| [List]&lt;Uint32&gt; | ownerIds |
| Uint8 | ownerType |
| [List]&lt;Uint32&gt; | destinationIds |
| Uint16 | dataType |
| [DateTime] | createdAfter |
| [DateTime] | createdBefore |
| [DateTime] | updatedAfter |
| [DateTime] | updatedBefore |
| Uint32 | referDataId |
| [List]&lt;[String]&gt; | tags |
| Uint8 | resultOrderColumn |
| Uint8 | resultOrder |
| [ResultRange](NEX-Common-Types#resultrange-structure) | resultRange |
| Uint8 | resultOption |
| Uint32 | minimalRatingFrequency |

## DataStoreSearchResult ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | totalCount |
| [List]&lt;[DataStoreMetaInfo]&gt; | result |
| Uint8 | totalCountType |

## DataStoreGetNotificationUrlParam ([Structure])
| Type | Name |
| --- | --- |
| [String] | previousUrl |

## DataStoreReqGetNotificationUrlInfo ([Structure])
| Type | Name |
| --- | --- |
| [String] | url |
| [String] | key |
| [String] | query |
| [Buffer] | rootCaCert |

## DataStoreGetNewArrivedNotificationsParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | lastNotificationId |
| Uint16 | limit |

## DataStoreNotificationV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | notificationId |
| Uint32 | dataId |

## DataStoreNotification ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | notificationId |
| Uint64 | dataId |

## DataStoreRateObjectParam ([Structure])
| Type | Name |
| --- | --- |
| Sint32 | ratingValue |
| Uint64 | accessPassword |

## DataStoreRatingTarget ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Sint8 | slot |

## DataStoreGetSpecificMetaParamV1 ([Structure])
| Type | Name |
| --- | --- |
| [List]&lt;Uint32&gt; | dataIds |

## DataStoreGetSpecificMetaParam ([Structure])
| Type | Name |
| --- | --- |
| [List]&lt;Uint64&gt; | dataIds |

## DataStoreSpecificMetaInfoV1 ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | dataId |
| Uint32 | ownerId |
| Uint32 | size |
| Uint16 | dataType |
| Uint16 | version |

## DataStoreSpecificMetaInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | ownerId |
| Uint32 | size |
| Uint16 | dataType |
| Uint32 | version |

## DataStoreTouchObjectParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint32 | lockId |
| Uint64 | accessPassword |

## DataStoreRatingLog ([Structure])
| Type | Name |
| --- | --- |
| Bool | isRated |
| Uint32 | pid |
| Sint32 | ratingValue |
| [DateTime] | lockExpirationTime |

## DataStorePersistenceInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | ownerId |
| Uint16 | persistenceSlotId |
| Uint64 | dataId |

## DataStorePasswordInfo ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | dataId |
| Uint64 | accessPassword |
| Uint64 | updatePassword |

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

## DataStorePersistenceTarget ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | ownerId |
| Uint16 | persistenceSlotId |

## DataStoreKeyValue ([Structure])
| Type | Name |
| --- | --- |
| [String] | key |
| [String] | value |

## DataStorePermission ([Structure])
| Type | Name |
| --- | --- |
| Uint8 | permission |
| [List]&lt;Uint32&gt; | recipientIds |

## DataStoreRatingInitParamWithSlot ([Structure])
| Type | Name |
| --- | --- |
| Sint8 | slot |
| [DataStoreRatingInitParam] | param |

## DataStorePersistenceInitParam ([Structure])
| Type | Name |
| --- | --- |
| Uint16 | persistenceSlotId |
| Bool | deleteLastObject |

## DataStoreChangeMetaCompareParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | comparisonFlag |
| [String] | name |
| [DataStorePermission] | permission |
| [DataStorePermission] | delPermission |
| Uint16 | period |
| [qBuffer] | metaBinary |
| [List]&lt;[String]&gt; | tags |
| Uint32 | referredCnt |
| Uint16 | dataType |
| Uint8 | status |

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

## DataStoreRatingInitParam ([Structure])
| Type | Name |
| --- | --- |
| Uint8 | flag |
| Uint8 | internalFlag |
| Uint8 | lockType |
| Sint64 | initialValue |
| Sint32 | rangeMin |
| Sint32 | rangeMax |
| Sint8 | periodHour |
| Sint16 | periodDuration |

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

[DataStorePrepareGetParamV1]: #datastorepreparegetparamv1-structure
[DataStoreReqGetInfo]: #datastorereqgetinfo-structure
[DataStorePreparePostParamV1]: #datastorepreparepostparamv1-structure
[DataStoreReqPostInfoV1]: #datastorereqpostinfov1-structure
[DataStoreCompletePostParamV1]: #datastorecompletepostparamv1-structure
[DataStoreDeleteParam]: #datastoredeleteparam-structure
[DataStoreChangeMetaParamV1]: #datastorechangemetaparamv1-structure
[DataStoreGetMetaParam]: #datastoregetmetaparam-structure
[DataStoreMetaInfo]: #datastoremetainfo-structure
[DataStorePrepareUpdateParam]: #datastoreprepareupdateparam-structure
[DataStoreReqUpdateInfo]: #datastorerequpdateinfo-structure
[DataStoreCompleteUpdateParam]: #datastorecompleteupdateparam-structure
[DataStoreSearchParam]: #datastoresearchparam-structure
[DataStoreSearchResult]: #datastoresearchresult-structure
[DataStoreGetNotificationUrlParam]: #datastoregetnotificationurlparam-structure
[DataStoreReqGetNotificationUrlInfo]: #datastorereqgetnotificationurlinfo-structure
[DataStoreGetNewArrivedNotificationsParam]: #datastoregetnewarrivednotificationsparam-structure
[DataStoreNotificationV1]: #datastorenotificationv1-structure
[DataStoreRatingTarget]: #datastoreratingtarget-structure
[DataStoreRateObjectParam]: #datastorerateobjectparam-structure
[DataStoreRatingInfo]: #datastoreratinginfo-structure
[DataStoreRatingInfoWithSlot]: #datastoreratinginfowithslot-structure
[DataStoreGetSpecificMetaParamV1]: #datastoregetspecificmetaparamv1-structure
[DataStoreSpecificMetaInfoV1]: #datastorespecificmetainfov1-structure
[DataStorePreparePostParam]: #datastorepreparepostparam-structure
[DataStoreTouchObjectParam]: #datastoretouchobjectparam-structure
[DataStoreRatingLog]: #datastoreratinglog-structure
[DataStoreReqPostInfo]: #datastorereqpostinfo-structure
[DataStorePrepareGetParam]: #datastorepreparegetparam-structure
[DataStoreCompletePostParam]: #datastorecompletepostparam-structure
[DataStoreNotification]: #datastorenotification-structure
[DataStoreGetSpecificMetaParam]: #datastoregetspecificmetaparam-structure
[DataStoreSpecificMetaInfo]: #datastorespecificmetainfo-structure
[DataStorePersistenceInfo]: #datastorepersistenceinfo-structure
[DataStoreReqGetAdditionalMeta]: #datastorereqgetadditionalmeta-structure
[DataStorePasswordInfo]: #datastorepasswordinfo-structure
[DataStoreChangeMetaParam]: #datastorechangemetaparam-structure
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
[DataStorePersistenceTarget]: #datastorepersistencetarget-structure
[DataStoreKeyValue]: #datastorekeyvalue-structure
[DataStorePermission]: #datastorepermission-structure
[DataStoreRatingInitParamWithSlot]: #datastoreratinginitparamwithslot-structure
[DataStorePersistenceInitParam]: #datastorepersistenceinitparam-structure
[DataStoreChangeMetaCompareParam]: #datastorechangemetacompareparam-structure
[GlobalTradeStationData]: #globaltradestationdata-structure
[GlobalTradeStationTradeKey]: #globaltradestationtradekey-structure
[GlobalTradeStationDownloadPokemonResult]: #globaltradestationdownloadpokemonresult-structure
[DataStoreRatingInitParam]: #datastoreratinginitparam-structure