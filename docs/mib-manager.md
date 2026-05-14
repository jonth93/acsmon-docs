# MIB Manager

Upload, parse, and manage SNMP MIB files

MIB files provide human-readable names and descriptions for SNMP OIDs. Upload MIBs to auto-resolve OID names throughout the platform.

### Uploading MIBs

Supports `.mib`, `.txt`, and `.my` file formats. Files are parsed to extract the OID tree structure, names, descriptions, syntax, and data types. Parsed OIDs are stored in JSON format for efficient lookup.

### Missing MIB Detection

When a polled OID cannot be resolved to any loaded MIB entry, it's logged to the missing MIBs table. Admin users receive notifications about unresolved OIDs so the appropriate MIB can be uploaded.

### Bulk Operations

Select multiple MIBs for bulk delete or bulk reparse. Reparsing is useful after the parser has been updated.
