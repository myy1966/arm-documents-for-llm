Table B12.2 Continued from previous page

| Request        | TagOp                    | Data state | Tag state             |
|----------------|--------------------------|------------|-----------------------|
| ReadUnique     | Invalid, Transfer, Fetch | SD, UD     | Invalid, Clean, Dirty |
| MakeReadUnique | Invalid                  | SC         | Invalid, Clean        |
| MakeReadUnique | Invalid                  | SD         | Invalid, Clean, Dirty |
| MakeReadUnique | Transfer ᵃ               | SC         | Clean                 |
| MakeReadUnique | Transfer ᵃ               | SD         | Clean, Dirty          |

- ᵃ To issue a MakeReadUnique with a TagOp value of Transfer, it is required that the Requester has copies of both the data and the tags.