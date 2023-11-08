# The JSON format for vCon - Conversation Data Container

This is the working area for the individual Internet-Draft, "The JSON format for vCon - Conversation Data Container".

* [Editor's Copy](https://dgpetrie.github.io/draft-petrie-vcon/#go.draft-petrie-vcon.html)
* [Datatracker Page](https://datatracker.ietf.org/doc/draft-petrie-vcon)
* [Individual Draft](https://datatracker.ietf.org/doc/html/draft-petrie-vcon)
* [Compare Editor's Copy to Individual Draft](https://dgpetrie.github.io/draft-petrie-vcon/#go.draft-petrie-vcon.diff)


## Contributing


> Note on this fork:
> 
> This draft proposal focuses on adapting the vCon object for use in carrier environments, and increasing portability between different classes of service providers. The specific focus is on the Parties, Dialog, and Attachment objects.
>
> Within Parties there are many field types that are effectively replicating the jCard standard (RFC 6350) as well as including servar field types which do not apply to many communication methods that could be captured using vCon (STIR PASSporT data, Identity Validation attestations).
> 
> Within Dialog there have been field types added which only apply to contact center applications, such as transfer counts and disposition.
> 
> The Attachment object has recieved the most attention as it can serve as a repository for all of the "channel focused" data through the use of a set of formal extenions, and be used at the same time to store vendor specific information about the conversation object.
> 
> This proposal outlines the modified Parties, Dialog, and Attachment objects, as well as several "channel focused" extension to the Attachment Object as well as the generic "Document" and "Custom" extension types. An Overview of the changes is included at the bottom of this README document.
>
> -CL


See the
[guidelines for contributions](https://github.com/dgpetrie/draft-petrie-vcon/blob/main/CONTRIBUTING.md).

Contributions can be made by creating pull requests.
The GitHub interface supports creating pull requests using the Edit (✏) button.


## Command Line Usage

Formatted text and HTML versions of the draft can be built using `make`.

```sh
$ make
```

Command line usage requires that you have the necessary software installed.  See
[the instructions](https://github.com/martinthomson/i-d-template/blob/main/doc/SETUP.md).

 # Alterations from parent Draft

## PARTY Object
Example:
```
{
    "party": [
        {
            "uri": "tel:+12345678901",
            "jcard": {
                "FN": "Alice",
                "Version": "4.0'
            }
        },
        {
            "uri": "tel:+19876543210",
            "jcard": {
                "FN": "Bob"
                "Version": "4.0"
            }
        }
    ]
}
```

As seen in the above Example the PARTY object has been changed significantly and now consists of *only* two top level items:

### URI
```
"uri": "" (String)
```
The URI object is a unique identifier for the party on the platform in which the dialog occoured. For example on a UCaaS platform a call between an internal agent and an outside party may be represented by the URI value `sip:100@companya.com` and `tel:18588675309`. Note that in the text example the two objects use different protocol identifiers intentionally to demonstrate the flexibility of the field. 

### JCARD
```
 "jcard": {} (Object, Optional)
```
This element contans a RFC 7905 compliant jCard entry containing known data about the party. This field is optional, as the system initially creating the vCon object may not have further details about a given party other than the contact uri from which the conversation originated. 

> #### Why jCard?
> Rather than expand the vCon format to house data on a given party, we reference RFC 7905 (and by extension RFC 6350) as they are mature and widely adopted standards for formatting known data about an individual or company. Additionally most applications that support customer data understand the vCard format for contacts allowing for easier integration in a vCon import/export tool. 
