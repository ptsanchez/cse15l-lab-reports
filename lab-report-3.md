# Lab Report 3

The grep command has numerous different options and ways to utilize its full functionality. Here are just some of them to help speed up efficiency with whatever uses you require.


## grep -i
```
$ grep -i 'hello' 911report/chapter-1.txt
    At 10:39, the Vice President updated the Secretary on the air threat conference: Vice President: There's been at least three instances here where we've had reports of aircraft approaching Washington-a 
couple were confirmed hijack. And, pursuant to the President's instructions I gave authorization for them to be taken out. Hello?
```
The -i option to grep searches for all the lines that contains the string in the quotations. This search is _case-insensitive_ so if you happen to forget if the string you are searching for has any upper case, -i disregards this and still searches for the string, a powerful tool. 

```
$ grep -i 'new york' government/Media/Major_Changes.txt
The New York City legal services program is undergoing a radical
for New York City (LSNY), has received federal funds that in turn
New Yorkers. LSNY's role has been generally limited to certain
in the Southern District of New York, seeking to block its
according to its spokesman Eric Kleiman because the New York
mechanism" for the New York City program. As the funding agency,
The New York Law Journal (NY) - Thursday, August 15, 2002
organizations with LSNY as the sole member. Under New York's
The New York Law Journal (NY) - Thursday, August 15, 2002
for New York City, 02-6199. But he added that many other groups
```
In this example, I searched for 'New York' but forgot to capitalize, a simple and understandable mistake. -i is extremely helpful because if you searched for something without knowing you had to capitalize in the first place, you would assume there is not match, when in reality there actually is.

Source for grep -i: [https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)

## grep -c
```
$ grep -c 'new york' government/Media/Major_Changes.txt
0
```
Using the previous example as reference, this command did a search for all the lines that contained the string 'new york'. Due to the fact that I did not capitalize, the output was 0. 

```
$ grep -c 'the' biomed/cc103.txt
213
```
On the other hand, this option to grep is very useful if we only wanted to count the lines of a certain string that we __know__ would be very prevalent in the file. Many grep options such as -i actully displays the entire lines that contain the string, but -c is simply counting the lines and returing just the count.

Source for grep -c: [https://www.geeksforgeeks.org/grep-command-in-unixlinux/](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
## grep -n
```
$ grep -n 'New York' government/Media/Terrorist_Attack.txt 
11:publico in the history of the New York State Unified Court
29:Street. He would later tell a New York Law Journal reporter of the
51:of the New York Fire Department. With reference to the devastation
62:University of New York campus in Buffalo on Oct. 15; and at Albany
74:City of New York and the New York State Bar Association will issue
77:of the City University of New York School of Law.
115:Court of New York, the nation's busiest. In landlord-tenant
123:in New York," Judge Lippman said in the release. "Ninety percent of
127:"[T]he New York State Access to Justice Center... will galvanize
139:differently in New York City, for instance, than upstate." He
154:Taking note of the generally conservative impulse of New York's
238:the New York firm Marcos & Negron LLP. Last year, the ABA
```
By using the -n, the command will search for all the lines in a file that match the given string but also accompanying it with the line number in the actual file. This is especially important if you wanted to sift through files in a quick matter, in which you could then locate the line number for future reference.

```
$ grep -n 'cell' biomed/cc1852.txt
19:        effects of the contrast material on nerve cells [ 10],
20:        which result from its osmotic effect after intracellular
96:          reproducibility of manual delineation was excellent, with
499:        infiltration of lung structures by inflammatory cells.
```
Due to the nature of how this command works, it similar to how one would use ctrl+f in a browser, searching a string on a page. For instance in this example, we see the list of line counts jump from 96 to 499. It would be practically impossible to try and go through all those lines manually since other grep options would just show that the line existed somewhere in the page, but this command shows you where exactly to look.

Source for grep -n: [https://man7.org/linux/man-pages/man1/grep.1.html](https://man7.org/linux/man-pages/man1/grep.1.html)

## grep -B
```
$ grep -B 2 'cell' biomed/cc1852.txt
        barrier, injection of contrast material increases brain
        oedema [ 6, 7, 8, 9]. This is due to the direct toxic
        effects of the contrast material on nerve cells [ 10],
        which result from its osmotic effect after intracellular
--
          section, right and left lung parenchyma were delineated
          using the roller ball of the computer. The
          reproducibility of manual delineation was excellent, with
--
        of extravascular lung water that accumulates in
        interstitial and alveolar compartments and by an
        infiltration of lung structures by inflammatory cells.
```
grep -B has more interesting behavior as this command finds all the lines that match with the given string, but also provides relative context by listing lines before the actual line with the matched string. This has many applications for searching strings in a file considering the fact that you can provide yourself with context surrounding the matched line.

```
$ grep -B 1 "Latin America and China" plos/journal.pbio.0020001.txt
        implied? A closer look at the trends over the last decade reveals important advances in
        developing countries. For example, Latin America and China, although representing,
```
A nice feature that this command implements is the ability to control the amount of lines that you want. This is helpful as depending on the situation, you might want to be provided context of the strings that are being matched, so you can change the amount of lines displayed to whatever you need whether that be 10 or 100.

Source for grep -B: [https://linuxhint.com/grep_command_linux/](https://linuxhint.com/grep_command_linux/)
