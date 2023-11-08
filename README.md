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

