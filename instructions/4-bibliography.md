# Phase 4. Bibliographic database, literature study

In this phase you will process the found information sources to a continuous introductory text about the chosen bachelor thesis subject. This is probably the phase that will require the most effort and time. 

Don't postpone taking this up, otherwise you will not timely reach your deadlines for the assignments at the end of the semester!

- Open the file `paper/bibliografie.bib` using JabRef.
- Add all found sources to your bibliography database. Pay attention to the following:
    - All necessary information is present (tab page Required Fields), e.g.
        - Electronic/Online/WWW sources must have a "url" and "urldate" field !
        - A Book should have a publisher;
        - An Article should have a Journal title, year and number;
        - ...
    - Author names should be in the correct format (`Surname, first Name and surname, first name and ...`)
    - Each source should have a unique Bibtex key (typically AuthorSurNameYear, e.g. Knuth1985)
    - Whether you have the PDF file, that you have properly stored in the designated directory in JabRef. Change the name of the PDF file into the Bibtexkey, so you can open it from inside JabRef.
    - Keep extra information about the source: the Abstract (introductory paragraph), key words, DOI code, comments, ...
- Write an introductory text about the chosen subject for your bachelor thesis based on your sources. From the start put the text in the right section where it belongs. Refer to your sources where appropriate using the proper LaTeX-command:
    - `\autocite{Bibtexkey}` => (Author, year)
    - `\textcite{Bibtexkey}` => Author (year)
- Compile the LaTeX file regularly and check the output!
    - Is the text easily readible? Have someone else read it too!
    - Are the references correctly inserted? 
    - Is de bibliography complete? Check that only sources that are reffered to from the text are listed in the bibliography. Can you find enough information about each reference to track it down? Is it obvious what source you are referring to? Are online sources provided with a visit date?