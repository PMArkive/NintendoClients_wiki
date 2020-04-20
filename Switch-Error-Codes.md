# Error Categories
| Error Codes | Description |
| --- | --- |
| 2124-XXXX | [Account services](#account-error-codes) |
| 2155-XXXX | [Curl (http requests)](#curl-error-codes) |
| 2181-XXXX | [DAuth (device authentication)](#dauth-error-codes) |
| 2306-XXXX | [NEX (game servers)](#nex-error-codes)<br>[Error descriptions](#nex-error-descriptions) |
| 2618-XXXX | [PIA (peer to peer)](#pia-error-codes) |
| 2815-XXXX | [Coral (voice chat)](#coral-error-codes) |

# Account Error Codes
| Error Codes | Description |
| --- | --- |
| 4600-4799 | [AAuth (application authentication)](#aauth-errors) |
| 5000-5249 | [BaaS (backend as a service)](#baas-errors) |
| 6000-6249 | [Account server errors](#account-server-errors) |
| 7000-7499 | [HTTP status errors](#http-errors) |
| Other | [Other account errors](#general-account-errors) |

## General Account Errors
| Error code | Description |
| --- | --- |
| 2124-0010 | BaaS or account server returned invalid error code |
| 2124-3001 | AAuth server returned error 0111 ("Application update is required.") |
| 2124-3120 | AAuth server returned invalid response but http status indicates success |

## AAuth Errors
| Error code | Description |
| --- | --- |
| 2124-4605 | ROM ID has been banned (0105) |
| 2124-4618 | Invalid parameter in request (0118) |
| 2124-4799 | AAuth server returned invalid error code |

## BaaS Errors
| Error code | Description |
| --- | --- |
| 2124-5000 | `invalid_params` |
| 2124-5001 | `invalid_request` |
| 2124-5002 | `invalid_device_account` |
| 2124-5003 | `invalid_ndas_app_authn_token` |
| 2124-5004 | `invalid_idp` |
| 2124-5005 | `invalid_idp_account` |
| 2124-5006 | `linked_user_not_found` |
| 2124-5007 | `invalid_friend_code_format` |
| 2124-5008 | `user_link_not_exist` |
| 2124-5009 | `invalid_raw_content` |
| 2124-5100 | `invalid_token` |
| 2124-5101 | `insufficient_scope` |
| 2124-5102 | `forbidden` |
| 2124-5103 | `unavailable_device_account` |
| 2124-5104 | `resource_is_not_found` |
| 2124-5105 | `method_not_allowed` |
| 2124-5106 | `not_acceptable_language` |
| 2124-5107 | `resource_already_exists` |
| 2124-5108 | `user_link_already_exists` |
| 2124-5109 | `precondition_failed` |
| 2124-5110 | `friend_code_unregenerable_state` |
| 2124-5111 | `banned_user` |
| 2124-5112 | `deleted_user` |
| 2124-5113 | `membership_required` |
| 2124-5114 | `banned_user_by_application` |
| 2124-5200 | `internal_server_error` |
| 2124-5210 | `could_not_confirm_membership` |
| 2124-5249 | `under_maintenance` |

## Account Server Errors
| Error codes | Request path |
| --- | --- |
| 6000-6099 | [`/connect/1.0.0/authorize`](#account-server-errors-(authorization-request)) |
| 6100-6199 | [`/connect/1.0.0/api/token`](#account-server-errors-(token-request)) |
| 6200-6249 | - [`/api/1.0.0/users/<id>/qrcode_param`](#account-server-errors-user-info-request)<br>- [`/2.0.0/users/me`](#account-server-errors-user-info-request) |

### Account Server Errors (Authorization Request)
| Error codes | Name | Detail |
| --- | --- | --- |
| 2124-6000 | `unauthorized_client` | |
| 2124-6001 | `access_denied` | |
| 2124-6003 | `access_denied` | `id_token_hint_invalid` |
| 2124-6004 | `access_denied` | `user_deleted` |
| 2124-6010 | `invalid_scope` | |
| 2124-6011 | `invalid_scope` | `scope_token_unknown` |
| 2124-6012 | `invalid_scope` | `scope_token_prohibited` |
| 2124-6020 | `server_error` | |
| 2124-6021 | `login_required` | |
| 2124-6022 | `login_required` | `user_not_logged_in` |
| 2124-6023 | `login_required` | `user_different_from_id_token_hint` |
| 2124-6030 | `consent_required` | |
| 2124-6031 | `interaction_required` | |
| 2124-6032 | `interaction_required` | `user_banned` |
| 2124-6033 | `interaction_required` | `user_suspended` |
| 2124-6034 | `interaction_required` | `user_terms_agreement_required` |
| 2124-6099 | `under_maintenance` | |

### Account Server Errors (Token Request)
| Error codes | Name | Detail |
| --- | --- | --- |
| 2124-6100 | `invalid_request` | |
| 2124-6101 | `invalid_client` | |
| 2124-6102 | `invalid_grant` | |
| 2124-6103 | `invalid_grant` | `user_deleted` |
| 2124-6104 | `invalid_grant` | `user_banned` |
| 2124-6105 | `invalid_grant` | `user_suspended` |
| 2124-6106 | `invalid_grant` | `user_withdrawn` |
| 2124-6107 | `invalid_grant` | `user_terms_agreement_required` |
| 2124-6120 | `invalid_scope` | |
| 2124-6121 | `invalid_scope` | `scope_token_unknown` |
| 2124-6122 | `invalid_scope` | `scope_token_prohibited` |
| 2124-6123 | `invalid_scope` | `scope_token_not_authorized` |
| 2124-6130 | `unauthorized_client` | |
| 2124-6131 | `unsupported_grant_type` | |
| 2124-6132 | `server_error` | |
| 2124-6199 | `under_maintenance` | |

### Account Server Errors (User Info Request)
| Error codes | Name |
| --- | --- |
| 2124-6200 | `invalid_token` |
| 2124-6201 | `insufficient_scope` |
| 2124-6249 | `under_maintenance` |

## HTTP Errors
| Error code | HTTP status |
| --- | --- |
| 2124-7000 | Invalid |
| 2124-7001 | Invalid (4xx) |
| 2124-7002 | Invalid (5xx) |
| 2124-7400 | 400 (Bad Request) |
| 2124-7401 | 401 (Unauthorized) |
| 2124-7403 | 403 (Forbidden) |
| 2124-7404 | 404 (Not Found) |
| 2124-7405 | 405 (Method Not Allowed) |
| 2124-7406 | 406 (Not Acceptable) |
| 2124-7407 | 407 (Proxy Authentication Required) |
| 2124-7408 | 408 (Request Timeout) |
| 2124-7409 | 409 (Conflict) |
| 2124-7410 | 410 (Gone) |
| 2124-7411 | 411 (Length Required) |
| 2124-7412 | 412 (Precondition Failed) |
| 2124-7413 | 413 (Payload Too Large) |
| 2124-7414 | 414 (URI Too Long) |
| 2124-7415 | 415 (Unsupported Media Type) |
| 2124-7416 | 416 (Requested Range Not Satisfiable) |
| 2124-7417 | 417 (Expectation Failed) |
| 2124-7500 | 500 (Internal Server Error) |
| 2124-7501 | 501 (Not Implemented) |
| 2124-7502 | 502 (Bad Gateway) |
| 2124-7503 | 503 (Service Unavailable) |
| 2124-7504 | 504 (Gateway Timeout) |
| 2124-7505 | 505 (HTTP Version Not Supported) |

# Curl Error Codes
| Error code | Description |
| --- | --- |
| 2155-8001 | CURLE_UNSUPPORTED_PROTOCOL |
| 2155-8002 | CURLE_FAILED_INIT |
| 2155-8003 | CURLE_URL_MALFORMAT |
| 2155-8004 | CURLE_NOT_BUILT_IN |
| 2155-8005 | CURLE_COULDNT_RESOLVE_PROXY |
| 2155-8006 | CURLE_COULDNT_RESOLVE_HOST |
| 2155-8007 | CURLE_COULDNT_CONNECT |
| 2155-8009 | CURLE_REMOTE_ACCESS_DENIED |
| 2155-8016 | CURLE_HTTP2 |
| 2155-8018 | CURLE_PARTIAL_FILE |
| 2155-8021 | CURLE_QUOTE_ERROR |
| 2155-8022 | CURLE_HTTP_RETURNED_ERROR |
| 2155-8023 | CURLE_WRITE_ERROR |
| 2155-8025 | CURLE_UPLOAD_FAILED |
| 2155-8026 | CURLE_READ_ERROR |
| 2155-8027 | CURLE_OUT_OF_MEMORY |
| 2155-8028 | CURLE_OPERATION_TIMEDOUT |
| 2155-8033 | CURLE_RANGE_ERROR |
| 2155-8034 | CURLE_HTTP_POST_ERROR |
| 2155-8035 | CURLE_SSL_CONNECT_ERROR |
| 2155-8036 | CURLE_BAD_DOWNLOAD_RESUME |
| 2155-8041 | CURLE_FUNCTION_NOT_FOUND |
| 2155-8042 | CURLE_ABORTED_BY_CALLBACK |
| 2155-8043 | CURLE_BAD_FUNCTION_ARGUMENT |
| 2155-8045 | CURLE_INTERFACE_FAILED |
| 2155-8047 | CURLE_TOO_MANY_REDIRECTS |
| 2155-8048 | CURLE_UNKNOWN_OPTION |
| 2155-8051 | CURLE_PEER_FAILED_VERIFICATION |
| 2155-8052 | CURLE_GOT_NOTHING |
| 2155-8053 | CURLE_SSL_ENGINE_NOTFOUND |
| 2155-8054 | CURLE_SSL_ENGINE_SETFAILED |
| 2155-8055 | CURLE_SEND_ERROR |
| 2155-8056 | CURLE_RECV_ERROR |
| 2155-8058 | CURLE_SSL_CERTPROBLEM |
| 2155-8059 | CURLE_SSL_CIPHER |
| 2155-8061 | CURLE_BAD_CONTENT_ENCODING |
| 2155-8063 | CURLE_FILESIZE_EXCEEDED |
| 2155-8064 | CURLE_USE_SSL_FAILED |
| 2155-8065 | CURLE_SEND_FAIL_REWIND |
| 2155-8066 | CURLE_SSL_ENGINE_INITFAILED |
| 2155-8067 | CURLE_LOGIN_DENIED |
| 2155-8075 | CURLE_CONV_FAILED |
| 2155-8076 | CURLE_CONV_REQD |
| 2155-8077 | CURLE_SSL_CACERT_BADFILE |
| 2155-8080 | CURLE_SSL_SHUTDOWN_FAILED |
| 2155-8081 | CURLE_AGAIN |
| 2155-8082 | CURLE_SSL_CRL_BADFILE |
| 2155-8083 | CURLE_SSL_ISSUER_ERROR |
| 2155-8088 | CURLE_CHUNK_FAILED |
| 2155-8089 | CURLE_NO_CONNECTION_AVAILABLE |
| 2155-8090 | CURLE_SSL_PINNEDPUBKEYNOTMATCH |
| 2155-8091 | CURLE_SSL_INVALIDCERTSTATUS |
| 2155-8092 | Curl returned error 94 (nintendo-specific) |
| 2155-8093 | Curl returned error 95 (nintendo-specific) |
| 2155-8094 | Curl returned error 96 (nintendo-specific) |
| 2155-8095 | Curl returned error 97 (nintendo-specific) |
| 2155-8096 | Curl returned error 98 (nintendo-specific) |
| 2155-8148 | Curl returned an invalid error code |
| 2155-8151 | CURLM_BAD_HANDLE |
| 2155-8152 | CURLM_BAD_EASY_HANDLE |
| 2155-8153 | CURLM_OUT_OF_MEMORY |
| 2155-8154 | CURLM_INTERNAL_ERROR |
| 2155-8155 | CURLM_BAD_SOCKET |
| 2155-8156 | CURLM_UNKNOWN_OPTION |
| 2155-8157 | CURLM_ADDED_ALREADY |
| 2155-8191 | Curl multi returned an invalid error code |

# DAuth Error Codes
| Error code | Description |
| --- | --- |
| 2181-0100 | Server returned invalid error code |
| 2181-3100 | Server returned invalid response |
| 2181-4008 | Server returned error 0008 ("Device has been banned.") |
| 2181-4014 | Server returned error 0014 ("Invalid parameter in request.") |

# NEX Error Codes
| Error code | Name |
| --- | --- |
| 2306-0102 | Core::Unknown |
| 2306-0103 | Core::NotImplemented |
| 2306-0104 | Core::InvalidPointer |
| 2306-0105 | Core::OperationAborted |
| 2306-0106 | Core::Exception |
| 2306-0107 | Core::AccessDenied |
| 2306-0108 | Core::InvalidHandle |
| 2306-0109 | Core::InvalidIndex |
| 2306-0110 | Core::OutOfMemory |
| 2306-0111 | Core::InvalidArgument |
| 2306-0112 | Core::Timeout |
| 2306-0113 | Core::InitializationFailure |
| 2306-0114 | Core::CallInitiationFailure |
| 2306-0115 | Core::RegistrationError |
| 2306-0116 | Core::BufferOverflow |
| 2306-0117 | Core::InvalidLockState |
| 2306-0118 | Core::InvalidSequence |
| 2306-0119 | Core::SystemError |
| 2306-0120 | Core::Cancelled |
| 2306-0201 | DDL::InvalidSignature |
| 2306-0202 | DDL::IncorrectVersion |
| 2306-0301 | RendezVous::ConnectionFailure |
| 2306-0302 | RendezVous::NotAuthenticated |
| 2306-0302 | RendezVous::InvalidUsername |
| 2306-0303 | RendezVous::InvalidPassword |
| 2306-0304 | RendezVous::UsernameAlreadyExists |
| 2306-0305 | RendezVous::AccountDisabled |
| 2306-0306 | RendezVous::AccountExpired |
| 2306-0307 | RendezVous::ConcurrentLoginDenied |
| 2306-0308 | RendezVous::EncryptionFailure |
| 2306-0309 | RendezVous::InvalidPID |
| 2306-0310 | RendezVous::MaxConnectionsReached |
| 2306-0311 | RendezVous::InvalidGID |
| 2306-0312 | RendezVous::InvalidControlScriptID |
| 2306-0313 | RendezVous::InvalidOperationInLiveEnvironment |
| 2306-0314 | RendezVous::DuplicateEntry |
| 2306-0315 | RendezVous::ControlScriptFailure |
| 2306-0316 | RendezVous::ClassNotFound |
| 2306-0317 | RendezVous::SessionVoid |
| 2306-0319 | RendezVous::DDLMismatch |
| 2306-0320 | RendezVous::InvalidConfiguration |
| 2306-0322 | RendezVous::SessionFull |
| 2306-0323 | RendezVous::InvalidGatheringPassword |
| 2306-0324 | RendezVous::WithoutParticipationPeriod |
| 2306-0325 | RendezVous::PersistentGatheringCreationMax |
| 2306-0326 | RendezVous::PersistentGatheringParticipationMax |
| 2306-0327 | RendezVous::DeniedByParticipants |
| 2306-0328 | RendezVous::ParticipantInBlackList |
| 2306-0329 | RendezVous::GameServerMaintenance |
| 2306-0330 | RendezVous::OperationPostpone |
| 2306-0331 | RendezVous::OutOfRatingRange |
| 2306-0332 | RendezVous::ConnectionDisconnected |
| 2306-0333 | RendezVous::InvalidOperation |
| 2306-0334 | RendezVous::NotParticipatedGathering |
| 2306-0335 | RendezVous::MatchmakeSessionUserPasswordUnmatch |
| 2306-0336 | RendezVous::MatchmakeSessionSystemPasswordUnmatch |
| 2306-0337 | RendezVous::UserIsOffline |
| 2306-0338 | RendezVous::AlreadyParticipatedGathering |
| 2306-0339 | RendezVous::PermissionDenied |
| 2306-0340 | RendezVous::NotFriend |
| 2306-0341 | RendezVous::SessionClosed |
| 2306-0342 | RendezVous::DatabaseTemporarilyUnavailable |
| 2306-0343 | RendezVous::InvalidUniqueId |
| 2306-0344 | RendezVous::MatchmakingWithdrawn |
| 2306-0345 | RendezVous::LimitExceeded |
| 2306-0346 | RendezVous::AccountTemporarilyDisabled |
| 2306-0347 | RendezVous::PartiallyServiceClosed |
| 2306-0348 | RendezVous::ConnectionDisconnectedForConcurrentLogin |
| 2306-0401 | PythonCore::Exception |
| 2306-0402 | PythonCore::TypeError |
| 2306-0403 | PythonCore::IndexError |
| 2306-0404 | PythonCore::InvalidReference |
| 2306-0405 | PythonCore::CallFailure |
| 2306-0406 | PythonCore::MemoryError |
| 2306-0407 | PythonCore::KeyError |
| 2306-0408 | PythonCore::OperationError |
| 2306-0409 | PythonCore::ConversionError |
| 2306-0410 | PythonCore::ValidationError |
| 2306-0501 | Transport::Unknown |
| 2306-0502 | Transport::ConnectionFailure |
| 2306-0503 | Transport::InvalidUrl |
| 2306-0504 | Transport::InvalidKey |
| 2306-0505 | Transport::InvalidURLType |
| 2306-0506 | Transport::DuplicateEndpoint |
| 2306-0507 | Transport::IOError |
| 2306-0508 | Transport::Timeout |
| 2306-0509 | Transport::ConnectionReset |
| 2306-0510 | Transport::IncorrectRemoteAuthentication |
| 2306-0511 | Transport::ServerRequestError |
| 2306-0512 | Transport::DecompressionFailure |
| 2306-0513 | Transport::ReliableSendBufferFullFatal |
| 2306-0514 | Transport::UPnPCannotInit |
| 2306-0515 | Transport::UPnPCannotAddMapping |
| 2306-0516 | Transport::NatPMPCannotInit |
| 2306-0517 | Transport::NatPMPCannotAddMapping |
| 2306-0519 | Transport::UnsupportedNAT |
| 2306-0520 | Transport::DnsError |
| 2306-0521 | Transport::ProxyError |
| 2306-0522 | Transport::DataRemaining |
| 2306-0523 | Transport::NoBuffer |
| 2306-0524 | Transport::NotFound |
| 2306-0525 | Transport::TemporaryServerError |
| 2306-0526 | Transport::PermanentServerError |
| 2306-0527 | Transport::ServiceUnavailable |
| 2306-0528 | Transport::ReliableSendBufferFull |
| 2306-0529 | Transport::InvalidStation |
| 2306-0530 | Transport::InvalidSubStreamID |
| 2306-0531 | Transport::PacketBufferFull |
| 2306-0532 | Transport::NatTraversalError |
| 2306-0533 | Transport::NatCheckError |
| 2306-0602 | DOCore::StationNotReached |
| 2306-0603 | DOCore::TargetStationDisconnect |
| 2306-0604 | DOCore::LocalStationLeaving |
| 2306-0605 | DOCore::ObjectNotFound |
| 2306-0606 | DOCore::InvalidRole |
| 2306-0607 | DOCore::CallTimeout |
| 2306-0608 | DOCore::RMCDispatchFailed |
| 2306-0609 | DOCore::MigrationInProgress |
| 2306-0610 | DOCore::NoAuthority |
| 2306-0611 | DOCore::NoTargetStationSpecified |
| 2306-0612 | DOCore::JoinFailed |
| 2306-0613 | DOCore::JoinDenied |
| 2306-0614 | DOCore::ConnectivityTestFailed |
| 2306-0615 | DOCore::Unknown |
| 2306-0616 | DOCore::UnfreedReferences |
| 2306-0617 | DOCore::JobTerminationFailed |
| 2306-0618 | DOCore::InvalidState |
| 2306-0619 | DOCore::FaultRecoveryFatal |
| 2306-0620 | DOCore::FaultRecoveryJobProcessFailed |
| 2306-0621 | DOCore::StationInconsitency |
| 2306-0622 | DOCore::AbnormalMasterState |
| 2306-0623 | DOCore::VersionMismatch |
| 2306-0701 | FPD::NotInitialized |
| 2306-0702 | FPD::AlreadyInitialized |
| 2306-0703 | FPD::NotConnected |
| 2306-0704 | FPD::Connected |
| 2306-0705 | FPD::InitializationFailure |
| 2306-0706 | FPD::OutOfMemory |
| 2306-0707 | FPD::RmcFailed |
| 2306-0708 | FPD::InvalidArgument |
| 2306-0709 | FPD::InvalidLocalAccountID |
| 2306-0710 | FPD::InvalidPrincipalID |
| 2306-0711 | FPD::InvalidLocalFriendCode |
| 2306-0712 | FPD::LocalAccountNotExists |
| 2306-0713 | FPD::LocalAccountNotLoaded |
| 2306-0714 | FPD::LocalAccountAlreadyLoaded |
| 2306-0715 | FPD::FriendAlreadyExists |
| 2306-0716 | FPD::FriendNotExists |
| 2306-0717 | FPD::FriendNumMax |
| 2306-0718 | FPD::NotFriend |
| 2306-0719 | FPD::FileIO |
| 2306-0720 | FPD::P2PInternetProhibited |
| 2306-0721 | FPD::Unknown |
| 2306-0722 | FPD::InvalidState |
| 2306-0724 | FPD::AddFriendProhibited |
| 2306-0726 | FPD::InvalidAccount |
| 2306-0727 | FPD::BlacklistedByMe |
| 2306-0729 | FPD::FriendAlreadyAdded |
| 2306-0730 | FPD::MyFriendListLimitExceed |
| 2306-0731 | FPD::RequestLimitExceed |
| 2306-0732 | FPD::InvalidMessageID |
| 2306-0733 | FPD::MessageIsNotMine |
| 2306-0734 | FPD::MessageIsNotForMe |
| 2306-0735 | FPD::FriendRequestBlocked |
| 2306-0736 | FPD::NotInMyFriendList |
| 2306-0737 | FPD::FriendListedByMe |
| 2306-0738 | FPD::NotInMyBlacklist |
| 2306-0739 | FPD::IncompatibleAccount |
| 2306-0740 | FPD::BlockSettingChangeNotAllowed |
| 2306-0741 | FPD::SizeLimitExceeded |
| 2306-0742 | FPD::OperationNotAllowed |
| 2306-0743 | FPD::NotNetworkAccount |
| 2306-0744 | FPD::NotificationNotFound |
| 2306-0745 | FPD::PreferenceNotInitialized |
| 2306-0746 | FPD::FriendRequestNotAllowed |
| 2306-1101 | Ranking::NotInitialized |
| 2306-1102 | Ranking::InvalidArgument |
| 2306-1103 | Ranking::RegistrationError |
| 2306-1105 | Ranking::NotFound |
| 2306-1106 | Ranking::InvalidScore |
| 2306-1107 | Ranking::InvalidDataSize |
| 2306-1109 | Ranking::PermissionDenied |
| 2306-1110 | Ranking::Unknown |
| 2306-1111 | Ranking::NotImplemented |
| 2306-0801 | Authentication::NASAuthenticateError |
| 2306-0802 | Authentication::TokenParseError |
| 2306-0803 | Authentication::HttpConnectionError |
| 2306-0804 | Authentication::HttpDNSError |
| 2306-0805 | Authentication::HttpGetProxySetting |
| 2306-0806 | Authentication::TokenExpired |
| 2306-0807 | Authentication::ValidationFailed |
| 2306-0808 | Authentication::InvalidParam |
| 2306-0809 | Authentication::PrincipalIdUnmatched |
| 2306-0810 | Authentication::MoveCountUnmatch |
| 2306-0811 | Authentication::UnderMaintenance |
| 2306-0812 | Authentication::UnsupportedVersion |
| 2306-0813 | Authentication::ServerVersionIsOld |
| 2306-0814 | Authentication::Unknown |
| 2306-0815 | Authentication::ClientVersionIsOld |
| 2306-0816 | Authentication::AccountLibraryError |
| 2306-0817 | Authentication::ServiceNoLongerAvailable |
| 2306-0818 | Authentication::UnknownApplication |
| 2306-0819 | Authentication::ApplicationVersionIsOld |
| 2306-0820 | Authentication::OutOfService |
| 2306-0821 | Authentication::NetworkServiceLicenseRequired |
| 2306-0822 | Authentication::NetworkServiceLicenseSystemError |
| 2306-0823 | Authentication::NetworkServiceLicenseError3 |
| 2306-0824 | Authentication::NetworkServiceLicenseError4 |
| 2306-1201 | DataStore::Unknown |
| 2306-1202 | DataStore::InvalidArgument |
| 2306-1203 | DataStore::PermissionDenied |
| 2306-1204 | DataStore::NotFound |
| 2306-1205 | DataStore::AlreadyLocked |
| 2306-1206 | DataStore::UnderReviewing |
| 2306-1207 | DataStore::Expired |
| 2306-1208 | DataStore::InvalidCheckToken |
| 2306-1209 | DataStore::SystemFileError |
| 2306-1210 | DataStore::OverCapacity |
| 2306-1211 | DataStore::OperationNotAllowed |
| 2306-1212 | DataStore::InvalidPassword |
| 2306-1213 | DataStore::ValueNotEqual |
| 2306-1500 | ServiceItem::Unknown |
| 2306-1501 | ServiceItem::InvalidArgument |
| 2306-1502 | ServiceItem::EShopUnknownHttpError |
| 2306-1503 | ServiceItem::EShopResponseParseError |
| 2306-1504 | ServiceItem::NotOwned |
| 2306-1505 | ServiceItem::InvalidLimitationType |
| 2306-1506 | ServiceItem::ConsumptionRightShortage |
| 2306-1801 | MatchmakeReferee::Unknown |
| 2306-1802 | MatchmakeReferee::InvalidArgument |
| 2306-1803 | MatchmakeReferee::AlreadyExists |
| 2306-1804 | MatchmakeReferee::NotParticipatedGathering |
| 2306-1805 | MatchmakeReferee::NotParticipatedRound |
| 2306-1806 | MatchmakeReferee::StatsNotFound |
| 2306-1807 | MatchmakeReferee::RoundNotFound |
| 2306-1808 | MatchmakeReferee::RoundArbitrated |
| 2306-1809 | MatchmakeReferee::RoundNotArbitrated |
| 2306-1901 | Subscriber::Unknown |
| 2306-1902 | Subscriber::InvalidArgument |
| 2306-1903 | Subscriber::OverLimit |
| 2306-1904 | Subscriber::PermissionDenied |
| 2306-2001 | Ranking2::Unknown |
| 2306-2002 | Ranking2::InvalidArgument |
| 2306-2003 | Ranking2::InvalidScore |
| 2306-2201 | Screening::Unknown |
| 2306-2202 | Screening::InvalidArgument |
| 2306-2203 | Screening::NotFound |

# NEX Error Descriptions
| Error&nbsp;code | Description |
| --- | --- |
| 2306-0102 | The reason for the error is unknown. |
| 2306-0103 | The operation is currently not implemented. |
| 2306-0104 | The operation specifies or accesses an invalid pointer. |
| 2306-0105 | The operation was aborted. |
| 2306-0106 | The operation raised an exception. |
| 2306-0107 | An attempt was made to access data in an incorrect manner. This may be due to inadequate permission or the data, file, etc. not existing. |
| 2306-0108 | The operation specifies or accesses an invalid DOHandle. |
| 2306-0109 | The operation specifies or accesses an invalid index. |
| 2306-0110 | The system could not allocate or access enough memory or disk space to perform the specified operation. |
| 2306-0111 | Invalid argument were passed with the operation. The argument(s) may be out of range or invalid. |
| 2306-0112 | The operation did not complete within the specified timeout for that operation. |
| 2306-0113 | Initialization of the component failed. |
| 2306-0114 | The call failed to initialize. |
| 2306-0115 | An error occurred during registration. |
| 2306-0116 | The buffer is too large to be sent. |
| 2306-0301 | Connection was unable to be established, either with the Rendez-Vous back end or a Peer. |
| 2306-0302 | The Principal could not be authenticated by the Authentication Service. |
| 2306-0303 | The Principal tried to log in with an invalid user name, i.e. the user name does not exist in the database. |
| 2306-0304 | The Principal either tried to log in with an invalid password for the provided user name or tried to join a Gathering with an invalid password. |
| 2306-0305 | The provided user name already exists in the database. All usernames must be unique. |
| 2306-0306 | The Principal's account still exists in the database but the account has been disabled. |
| 2306-0307 | The Principal's account still exists in the database but the account has expired. |
| 2306-0308 | The Principal does not have the Capabilities to perform concurrent log ins, i.e. at any given time only one log-in may be maintained. |
| 2306-0309 | Data encryption failed. |
| 2306-0310 | The operation specifies or accesses an invalid PrincipalID. |
| 2306-0311 | Maximum connnection number is reached |
| 2306-0501 | The reason for the error is unknown. |
| 2306-0502 | Network connection was unable to be established. |
| 2306-0503 | The URL contained in the StationURL is invalid. The syntax may be incorrect. |
| 2306-0504 | The key used to authenticate a given station is invalid. The secure transport layer uses secret-key based cryptography to ensure the integrity and confidentiality of data sent across the network. |
| 2306-0505 | The specified transport type is invalid. |
| 2306-0506 | The Station is already connected via another EndPoint. |
| 2306-0507 | The data coudl not be sent across the network. This could be due to an invalid message, packet, or buffer. |
| 2306-0508 | The operation did not complete within the specified timeout for that operation. |
| 2306-0509 | The network connection was reset. |
| 2306-0510 | The destination Station did not authenticate itself properly. |
| 2306-0511 | 3rd-party server or device answered with an error code according to protocol used e.g. HTTP error code |

# PIA Error Codes
| Error Code | Name |
| --- | --- |
| 2618-0000 | ResultSdkViewerResultError |
| 2618-0001 | ResultAllocationFailed |
| 2618-0002 | ResultAlreadyInitialized |
| 2618-0003 | ResultBufferShortage |
| 2618-0004 | ResultBrokenData |
| 2618-0005 | ResultCancelled |
| 2618-0006 | ResultNetworkConnectionIsLost |
| 2618-0007 | ResultInvalidArgument |
| 2618-0008 | ResultInvalidState |
| 2618-0009 | ResultNoData |
| 2618-0010 | ResultNotFound |
| 2618-0011 | ResultNotImplemented |
| 2618-0012 | ResultNotInitialized |
| 2618-0013 | ResultBufferIsFull |
| 2618-0014 | ResultTimeOut |
| 2618-0015 | ResultAlreadyExists |
| 2618-0016 | ResultContainerIsFull |
| 2618-0017 | ResultTemporaryUnavailable |
| 2618-0019 | ResultNotSet |
| 2618-0101 | ResultMemoryLeak |
| 2618-0201 | ResultNatCheckFailed |
| 2618-0202 | ResultInUse |
| 2618-0203 | ResultDnsFailed |
| 2618-0302 | ResultInvalidNode |
| 2618-0304 | ResultNegligibleFault |
| 2618-0305 | ResultInvalidConnection |
| 2618-0308 | ResultErrorOccurred |
| 2618-0309 | ResultNetworkIsNotFound |
| 2618-0310 | ResultNetworkIsFull |
| 2618-0311 | ResultLocalLowerVersion |
| 2618-0312 | ResultLocalHigherVersion |
| 2618-0313 | ResultWifiOff |
| 2618-0314 | ResultSleep |
| 2618-0315 | ResultWirelessControllerCountLimitation |
| 2618-0401 | ResultConnectionFailed |
| 2618-0402 | ResultCreateStationFailed |
| 2618-0403 | ResultIncompatibleFormat |
| 2618-0404 | ResultNotInCommunication |
| 2618-0405 | ResultTableIsFull |
| 2618-0501 | ResultJoinRequestDenied |
| 2618-0502 | ResultStationConnectionFailed |
| 2618-0506 | ResultMeshIsFull |
| 2618-0507 | ResultInvalidSystemMessage |
| 2618-0510 | ResultStationConnectionNatTraversalFailedUnknown |
| 2618-0513 | ResultNatTraversalFailedBothEim |
| 2618-0514 | ResultNatTraversalFailedBothEdm |
| 2618-0515 | ResultNatTraversalFailedLocalEimRemoteEdm |
| 2618-0516 | ResultNatTraversalFailedLocalEdmRemoteEim |
| 2618-0517 | ResultRelayFailedNoCandidate |
| 2618-0518 | ResultRelayFailedRttLimit |
| 2618-0519 | ResultRelayFailedRelayNumLimit |
| 2618-0520 | ResultRelayFailedUnknown |
| 2618-0521 | ResultNatTraversalRequestTimeout |
| 2618-0541 | ResultSessionIsNotFound |
| 2618-0542 | ResultMatchmakeSessionIsFull |
| 2618-0543 | ResultDeniedByParticipants |
| 2618-0544 | ResultParticipantInBlockList |
| 2618-0545 | ResultSessionUserPasswordUnmatch |
| 2618-0546 | ResultSessionSystemPasswordUnmatch |
| 2618-0547 | ResultMeshConnectionIsLost |
| 2618-0548 | ResultSessionIsClosed |
| 2618-0549 | ResultCompanionStationIsOffline |
| 2618-0550 | ResultHostIsNotFriend |
| 2618-0551 | ResultSessionConnectionIsLost |
| 2618-0552 | ResultCompanionStationIsLeft |
| 2618-0554 | ResultSessionMigrationFailed |
| 2618-0555 | ResultSessionWrongState |
| 2618-0561 | ResultGameServerMaintenance |
| 2618-0562 | ResultGameServerProcessAborted |
| 2618-0571 | ResultCreateCommunityFailedUpperLimit |
| 2618-0572 | ResultJoinCommunityFailedUpperLimit |
| 2618-0573 | ResultCommunityIsFull |
| 2618-0574 | ResultCommunityIsNotFound |
| 2618-0575 | ResultCommunityIsClosed |
| 2618-0576 | ResultCommunityUserPasswordUnmatch |
| 2618-0577 | ResultAlreadyJoinedCommunity |
| 2618-0578 | ResultUserAccountNotExisted |
| 2618-0579 | ResultNetworkConnectionIsLostByDuplicateLogin |
| 2618-0583 | ResultNatTraversalFailedBothEimSamePublicAddress |
| 2618-0584 | ResultNatTraversalFailedBothEdmSamePublicAddress |
| 2618-0585 | ResultNatTraversalFailedLocalEimRemoteEdmSamePublicAddress |
| 2618-0586 | ResultNatTraversalFailedLocalEdmRemoteEimSamePublicAddress |
| 2618-0590 | ResultLicenseForNetworkServiceNotAvailable |
| 2618-0591 | ResultLicenseForNetworkServiceError |
| 2618-0592 | ResultLicenseForNetworkServiceSubscriptionError |
| 2618-0593 | ResultLicenseForNetworkServiceSubscriptionError2 |
| 2618-0602 | ResultDataIsNotArrivedYet |
| 2618-0606 | ResultDataIsNotSet |
| 2618-0701 | ResultLanLowerVersion |
| 2618-0702 | ResultLanHigherVersion |
| 2618-1001 | ResultSdkError |
| 2618-1003 | ResultCancelledByUser |

# Coral Error Codes
| Error code | Name |
| --- | --- |
| 2815-2101 | SmartDeviceVoiceChat::Unknown |
| 2815-2102 | SmartDeviceVoiceChat::InvalidArgument |
| 2815-2103 | SmartDeviceVoiceChat::InvalidResponse |
| 2815-2104 | SmartDeviceVoiceChat::InvalidAccessToken |
| 2815-2105 | SmartDeviceVoiceChat::Unauthorized |
| 2815-2106 | SmartDeviceVoiceChat::AccessError |
| 2815-2107 | SmartDeviceVoiceChat::UserNotFound |
| 2815-2108 | SmartDeviceVoiceChat::RoomNotFound |
| 2815-2109 | SmartDeviceVoiceChat::RoomNotActivated |
| 2815-2110 | SmartDeviceVoiceChat::ApplicationNotSupported |
| 2815-2111 | SmartDeviceVoiceChat::InternalServerError |
| 2815-2112 | SmartDeviceVoiceChat::ServiceUnavailable |
| 2815-2113 | SmartDeviceVoiceChat::UnexpectedError |
| 2815-2114 | SmartDeviceVoiceChat::UnderMaintenance |
| 2815-2115 | SmartDeviceVoiceChat::ServiceNoLongerAvailable |
| 2815-2116 | SmartDeviceVoiceChat::AccountTemporarilyDisabled |
| 2815-2117 | SmartDeviceVoiceChat::PermissionDenied |
| 2815-2118 | SmartDeviceVoiceChat::NetworkServiceLicenseRequired |
| 2815-2119 | SmartDeviceVoiceChat::AccountLibraryError |
| 2815-2120 | SmartDeviceVoiceChat::GameModeNotFound |