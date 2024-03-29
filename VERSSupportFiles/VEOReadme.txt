This zip file is a VERS Encapsulated Object (VEO). VEO files are
specified in specifications associated with Public Record Office Victoria (PROV)
Standard PROS 19/05 "Create, Capture and Control Standard". As at
2020 this Standard was available from
https://prov.vic.gov.au/recordkeeping-government/document-library/pros-1905-create-capture-and-control-standard

The two specifications are Constructing VEOs (PROS 19/05 S4) and Adding
Metadata Packages to VEOs (PROS 19/05 S5).

This VEOReadme.txt file contains a summary of the information in
PROS 19/05 S4.

This zip file contains a collection of information that it is desired to
keep accessible for a long period. The content of this information is
contained in subdirectories of this directory. The metadata that
organises and describes the information is contained in the
VEOContent.xml file.

The VEOContent.xml file contains one or more Information Objects - each
of which is a logical collection of information. Information Objects
may contain one or more Information Pieces. An Information Piece
represents a piece of information contained in this VEO. An Information
Piece includes references to at least one physical file (a Content File)
that actually represent the content. If more than one Content File is
present, this represents the same information expressed using different
software formats.

The XML elements in the VEOContent file are:
*	VEOVersion. The version of this Standard. This should be '3.0'.
*	HashFunctionAlgorithm. The hash function used to calculate the
	hash values stored in HashValue (see below)
*	InformationObject. A logical collection of information in this
	VEO.
*	InformationObjectType. A text label describing the purpose of
	this Information Object.
*	InformationObjectDepth. If the VEO contains more than one
	Information Object, the Information Objects may be organised in
	a tree. The sequence of Information Objects in the
	VEOContent.xml file will form a depth first traversal of this
	tree, and InformationObjectDepth is the depth of this
	particular Information Object in the tree.
*	MetadataPackage. This is a collection of metadata describing
	the Information Object. An Information Object may have multiple
	Metadata Packages.
*	MetadataSchemaIdentifier. This is used to identify the type of
	this Metadata Package.
*	MetadataSyntaxIdentifier. This is used to identify the way of
	representing the metadata package in XML. We encourage the use
	of RDF.
*	InformationPiece. This is a piece of information content within
	the Information Object.
*	Label. This is a text string that labels the Information Piece.
*	ContentFile. This represents a specific file in the VEO that
	represents the content of the InformationPiece.
*	ContentFilePathName. This is the file name of the file that
	contains the content. It is relative to this directory.
*	HashValue. The hash value resulting from applying the specified
	hash function (see HashFunctionAlgorithm above) to the sequence
	of octets forming the file.

The VEOContentSignature?.xml (where '?' is a number) files each contain
a digital signature that allows detection of corruption of the
VEOContent.xml file (and because the VEOContent.xml file includes hash
values of the content files, corruption of the content files as well).
The signature is generated by reading the VEOContent.xml file as a
sequence of octets and applying specified signature algorithm. The
contents of a VEOContentSignaturen.xml file are:
*	SignatureAlgorithm. This identifies the hash algorithm and the
	digital signature algorithm used to generate the signature.
*	SignatureDateTime. The date and time the signature was applied.
	Expressed in ISO8601.
*	Signer. A text string naming the person or organisation that
	created the digital signature
*	Signature. The resulting signature, encoded as Base64.
*	CertificateValue. An X.509 DER encoded certificate encoded as
Base64. The first certificate contains the public key used to validate
the signature. The second certificate contains the public key used to
validate the first certificate (and so on). The last certificate must
be self signed.

The VEOHistory.xml file contains a summary of events in the life of
this VEO. The elements in this file are:
*	VEOVersion. The version of this Standard. This should be '3.0'.
*	Event. A collection of information about an event in the life
	of this VEO.
*	EventDateTime. The date and time the event occurred. Expressed
	in ISO8601.
*	EventType. The a text string labelling the type of the event.
*	Initiator. The person or organisation that authorised or
	initiated this event.
*	Description. A text description of the event.
*	Errors. Any error resulting from this event.

The VEOHistorySignature?.xml (where '?' is a number) files each contain
a digital signature that allows detection of corruption of the
VEOHistory.xml file. The contents and method of generation of a
VEOHistorySignature file is identical to a VEOContentSignature file.
