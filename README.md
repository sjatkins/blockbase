# blockbase
The idea is to have a block oriented database in UOP style - that is it includes UOP style database metadata.

A block oriented database of this kind can exist in memory or backed by a file system or backed by various types of cloud artifacts such as S3 or other object store.

An interest possibility of any memory casche containing some subpart of larger block database.

## General Block Characteristics
### Header
Header identifies
- type of block
- next linked block
- empty space in block

## Special Blocks
### Index
These blocks map an external index to a block index and offset.  Among other things this makes compaction easy.  This is a specxal case of B* Index
### B* Tree Index
Each block contains N index_value, pointer pairs and a pointer to parent and sibling blocks.  This allows indexing of data in the database. 
### Class Descriptions
Description of structured data instances and their attributes, and pointer to first instance block
### Tag Description
Tag instances with their names and ids
### Group Description
Group instances with their containing groups, names and ids
### Relations Description
Relationships with their role, reverse role, restrictions on subject and object
### Tagged
pairs of tag_id, object_id
### Grouped
pairs of group_id, group_or_object_id
### Related
triples of subject_id, role_id, object_id
Alternately somewhat redundant pairs of <role_id, subject_or_object_id>, {s: s is related by role_id to sobject_or_object_id
### Instance
Block contains instances of a single class
### Variable Length
This type of block stores variable length data where a single data item may span multiple blocks.  There will be subtypes for specialized cases like mimetypes such as video or audio, strings/bytes, list[<type>] etc. 
  
