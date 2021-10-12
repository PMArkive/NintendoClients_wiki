You may be surprised to see the real names of parameter and structure members on many of the pages that describe NEX protocols. NEX has automatically generated the code that encodes/decodes method parameters and structures from a data definition language (DDL), and many games contain the parse tree of the DDL declarations in their data segment. It's encoded in big-endian byte order (regardless of the platform) and looks as follows:

| Type | Description |
| --- | --- |
| Uint32 | Magic number (0xCD652312) |
| Uint8 | Unknown (always 0) |
| Uint32 | Major version |
| Uint32 | Minor version |
| Uint32 | Micro version |
| Uint32 | Build version |
| [NameSpace] | Root namespace |

## NameSpace
| Type | Description |
| --- | --- |
| Uint32 | Number of elements (N) |
| [Element](#element) (N) | Namespace elements |

### Element
| Type | Description |
| --- | --- |
| Uint8 | Type id |
| | Body |

| ID | Type |
| --- | --- |
| 1 | [NameSpaceItem] |
| 2 | [Declaration] |
| 3 | DOClassDeclaration |
| 4 | DatasetDeclaration |
| 5 | [TypeDeclaration] |
| 6 | Variable |
| 8 | RMC |
| 9 | Action |
| 10 | AdapterDeclaration |
| 11 | [PropertyDeclaration] |
| 12 | ProtocolDeclaration |
| 13 | Parameter |
| 14 | ReturnValue |
| 15 | [ClassDeclaration] |
| 16 | TemplateDeclaration |
| 17 | SimpleTypeDeclaration |
| 18 | [TemplateInstance] |
| 19 | [DDLUnitDeclaration] |
| 20 | DupSpaceDeclaration |

## String
| Type | Description |
| --- | --- |
| Uint32 | Length (N) |
| Bytes (N) | String (without null terminator) |

## NameSpaceRef
| Type | Description |
| --- | --- |
| [String] | Name |
| [NameSpace] | Namespace |

## ParseTreeItem
| Type | Description |
| --- | --- |
| [String] | Name |

## NameSpaceItem
The second parse tree item is always the same as the first parse tree item. I don't know why it's stored twice.

| Type | Description |
| --- | --- |
| [ParseTreeItem] | Parse tree item |
| [ParseTreeItem] | Parse tree item |

## Declaration
| Type | Description |
| --- | --- |
| [NameSpaceItem] | Name space item |
| [String] | DDL unit name |
| [Namespace] | Properties |

## TypeDeclaration
| Type | Description |
| --- | --- |
| [Declaration] | Declaration |

## PropertyDeclaration
| Type | Description |
| --- | --- |
| [Declaration] | Declaration |
| Uint32 | Category mask |
| Uint32 | Allowed target mask |

## ClassDeclaration
| Type | Description |
| --- | --- |
| [TypeDeclaration] | Type declaration |
| [NameSpaceRef] | Namespace ref |

## TemplateInstance
| Type | Description |
| --- | --- |
| [TypeDeclaration] | Type declaration |
| [String] | Base type name |
| Uint32 | Number of template arguments (N) |
| [String] (N) | Template arguments |

## DDLUnitDeclaration
| Type | Description |
| --- | --- |
| [Declaration] | Declaration |
| [String] | Unit name |
| [String] | Unit dir |

[ClassDeclaration]: #classdeclaration
[DDLUnitDeclaration]: #ddlunitdeclaration
[Declaration]: #declaration
[NameSpace]: #namespace
[NameSpaceItem]: #namespaceitem
[NameSpaceRef]: #namespaceref
[ParseTreeItem]: #parsetreeitem
[PropertyDeclaration]: #propertydeclaration
[String]: #string
[TemplateInstance]: #templateinstance
[TypeDeclaration]: #typedeclaration