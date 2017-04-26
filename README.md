# LilyPond Export

In this repository I am creating an export-infrastructure for LilyPond.
The files presented here are far from production-ready, but at least the functions provided here can
create humdrum and musicXML for very simple scores.

*ISSUE humdrum and musicXML both have to be included!*

In this first proof of concept a file

```lilypond
\version "2.19.60"
\include "export-humdrum.ly"
\include "export-musicXML.ly"


\runTranslator
<<
  \new Staff {
    \time 3/4
    \relative <<
      { c''4. a8 g4 | g bes <g b> | a c a | } \\
      { e8 f g fis e4 | es2 d4 | <c e>2 <c f>4 }
    >>
  }
  \new Staff {
    \time 3/4
    \relative { c'2 c4 | c g' b, | a2. | }
  }
>>
\FileExport #`((exporter . ,exportMusicXML))
```
creates an XML-file:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE score-partwise PUBLIC "-//Recordare//DTD MusicXML 3.0 Partwise//EN" "http://www.musicxml.org/dtds/partwise.dtd">
<score-partwise version="3.0">
  <part-list>
    <score-part id="P1">
      <part-name>Part 1</part-name>
    </score-part>
    <score-part id="P2">
      <part-name>Part 2</part-name>
    </score-part>
  </part-list>
  <part id="P1">
    <measure number="1">
      <attributes>
	<divisions>8</divisions>
	<time><beats>3</beats><beat-type>4</beat-type></time>
      </attributes>
      <note>
	<pitch>
	  <step>E</step>
	  <octave>4</octave>
	</pitch>
	<duration>4</duration>
	<voice>2</voice>
	<type>eighth</type>
	<beam number="1">begin</beam>
      </note>
      <note>
	<pitch>
	  <step>F</step>
	  <octave>4</octave>
	</pitch>
	<duration>4</duration>
	<voice>2</voice>
	<type>eighth</type>
	<beam number="1">continue</beam>
      </note>
      <note>
	<pitch>
	  <step>G</step>
	  <octave>4</octave>
	</pitch>
	<duration>4</duration>
	<voice>2</voice>
	<type>eighth</type>
	<beam number="1">continue</beam>
      </note>
      <note>
	<pitch>
	  <step>F</step>
	  <alter>1</alter>
	  <octave>4</octave>
	</pitch>
	<duration>4</duration>
	<voice>2</voice>
	<type>eighth</type>
	<beam number="1">end</beam>
      </note>
      <note>
	<pitch>
	  <step>E</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>2</voice>
	<type>quarter</type>
      </note>
      <backup><duration>24</duration></backup>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>5</octave>
	</pitch>
	<duration>12</duration>
	<voice>1</voice>
	<type>quarter</type>
	<dot/>
      </note>
      <note>
	<pitch>
	  <step>A</step>
	  <octave>4</octave>
	</pitch>
	<duration>4</duration>
	<voice>1</voice>
	<type>eighth</type>
      </note>
      <note>
	<pitch>
	  <step>G</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
    </measure>
    <measure number="2">
      <attributes>
	<divisions>8</divisions>
      </attributes>
      <note>
	<pitch>
	  <step>E</step>
	  <alter>-1</alter>
	  <octave>4</octave>
	</pitch>
	<duration>16</duration>
	<voice>2</voice>
	<type>half</type>
      </note>
      <note>
	<pitch>
	  <step>D</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>2</voice>
	<type>quarter</type>
      </note>
      <backup><duration>24</duration></backup>
      <note>
	<pitch>
	  <step>G</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<pitch>
	  <step>B</step>
	  <alter>-1</alter>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<pitch>
	  <step>G</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<chord />
	<pitch>
	  <step>B</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
    </measure>
    <measure number="3">
      <attributes>
	<divisions>8</divisions>
      </attributes>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>4</octave>
	</pitch>
	<duration>16</duration>
	<voice>2</voice>
	<type>half</type>
      </note>
      <note>
	<chord />
	<pitch>
	  <step>E</step>
	  <octave>4</octave>
	</pitch>
	<duration>16</duration>
	<voice>2</voice>
	<type>half</type>
      </note>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>2</voice>
	<type>quarter</type>
      </note>
      <note>
	<chord />
	<pitch>
	  <step>F</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>2</voice>
	<type>quarter</type>
      </note>
      <backup><duration>24</duration></backup>
      <note>
	<pitch>
	  <step>A</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>5</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<pitch>
	  <step>A</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
    </measure>
  </part>
  <part id="P2">
    <measure number="1">
      <attributes>
	<divisions>8</divisions>
	<time><beats>3</beats><beat-type>4</beat-type></time>
      </attributes>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>4</octave>
	</pitch>
	<duration>16</duration>
	<voice>1</voice>
	<type>half</type>
      </note>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
    </measure>
    <measure number="2">
      <attributes>
	<divisions>8</divisions>
      </attributes>
      <note>
	<pitch>
	  <step>C</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<pitch>
	  <step>G</step>
	  <octave>4</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
      <note>
	<pitch>
	  <step>B</step>
	  <octave>3</octave>
	</pitch>
	<duration>8</duration>
	<voice>1</voice>
	<type>quarter</type>
      </note>
    </measure>
    <measure number="3">
      <attributes>
	<divisions>8</divisions>
      </attributes>
      <note>
	<pitch>
	  <step>A</step>
	  <octave>3</octave>
	</pitch>
	<duration>24</duration>
	<voice>1</voice>
	<type>half</type>
	<dot/>
      </note>
    </measure>
  </part>
</score-partwise>
```


