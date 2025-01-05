## Framing 
To make it easier to send data it's divided into smaller chunks called `frame` , There are 2 ways to determine the start and end of the frame:
- ### Character Stuffing:
  A special character are used to mark the start and end of the frame , if the special character occures in the data . it's 'stuffed' with an escape sequence to avoid confusion
- ### Bit stuffing
  A special bit pattern (link 1111) marks the frame , if the special bit occures in the data, '0' is added to break the pattern and makes sure that it not mistaken as end of frame
