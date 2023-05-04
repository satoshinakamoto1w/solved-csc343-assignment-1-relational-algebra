Download Link: https://assignmentchef.com/product/solved-csc343-assignment-1-relational-algebra
<br>
You will be working on a schema and queries for a database used by a zoological institute to track an archive of their artifacts.

During a eld trip collectors gather a variety of artifacts of the animals they study, resulting in tissue samples, images, physical models (such as casts of paw prints), or live colonies.

After arriving at the institute, artifacts must be safely stored and maintained by technicians. Some artifacts are cited in one or more publications. In all cases the o cial species name must be recorded, and must appear in the <a href="https://www.catalogueoflife.org/">Catalogue of Life database</a><a href="https://www.catalogueoflife.org/">.</a> If correct taxonomic practices are followed, each species belongs to exactly one genus, and each genus to exactly one family. Tables COL, Genus, and Species are derived from Catalogue of Life database. relations

Collection(<u>CID</u>, date, SID)

Tuples here represent entire collections from a eld trip, where CID is the collection ID, date is the starting date of the eld trip, and SID is the sta ID of the collector.

Collected(CID, AN)

A tuple here represents the fact that collection CID includes artifact number AN. A single collection usually contains multiple artifacts, and a single artifact may be aggregated from more than one collection.

Artifact(<u>AN</u>, species, type, location, SID)

Tuples here represent single artifact collected in the eld. AN is the artifact number, species is the scienti c species name, type is one of tissue, image, model, or live, location is where it was collected, and SID is the sta number of the technician who maintains this artifact.

Published(AN, journal, date)

A tuple here represents the fact that artifact AN was mentioned in scholarly publication journal with publication date date.

Sta (<u>SID</u>, name, email, rank, date)

These tuples represent a member of the institute’s scienti c sta . SID is the sta ID, name is their full name, email is their professional email, rank is one of: technician, student, pre-tenure, or tenured, and date is the date when they attained that rank.

COL(family)

A singleton tuple here means that family is a scienti c zoological family name that appears in the Catalogue of Life.

Genus(genus, family)

A tuple here means that genus is in family family.

Species(species, genus)

A tuple here means that species is in genus genus.

<h1>our constraints</h1>

For each of the following constraints give a one sentence explanation of what the constraint implies, and why it is required.

species(Artifact) <sub>species</sub>(Species) = ;. rank(Staff) f’technician’, ’student’, ’pre-tenure’, ’tenure’g.

family(Genus)           <sub>family</sub>(COL) = ;. genus(Species)          <sub>genus</sub>(Genus).

CID(Collected) =          <sub>CID</sub>(Collection).

AN(Artifact) =          <sub>AN</sub>(Collected).

SID(Collection)               <sub>SID</sub>(Staff).

SID(Artifact)               <sub>SID</sub>(Staff).

type(Artifact) f<sup>0</sup>tissue<sup>0</sup>;<sup>0 </sup>image<sup>0</sup>;<sup>0 </sup>model<sup>0</sup>;<sup>0 </sup>live<sup>0</sup>g

AN(Published)             <sub>AN</sub>(Artifact)

<h1>queries</h1>

Write relational algebra expressions for each of the queries below. You must use notations from this course and operators:

; ; ;./;./<sub>condition</sub>;              ;;[;               ;= You may also use constants:

today (for current date)            ; (for the empty set)

In your queries pay attention to the following:

All relations are sets, and you may only use relational algebra operators covered in Chapter 2 of the course text.

Do not make assumptions that are not enforced by our constraints above, so your queries should work correctly for any database that obeys our schema and constraints.

Other than constants such as 23 or “lupus”, a select operation only examines values contained in a tuple, not aggregated over an entire column.

Your selection conditions can use arithmetic operators, such as +; ;6=; ;&gt;;&lt; and friends. You can use logical operators such as _;^, and :, and treat dates and numeric attributes as numbers that you can perform arithmetic on.

Use good variable names and provide lots of comments to explain your intentions.

Return multiple tuples if that is appropriate for your query.

There may be a query or queries that cannot be expressed in the relational algebra you have been taught so far, in which case just write cannot be expressed.” The queries below are not in any particular order.

<ol>

 <li>Rationale: Performance reviews include seeing how current the work is of sta who have held their current rank for a long time.</li>

</ol>

Query: Find the most recent collection date of any artifact collected by a sta member who has held their current rank the longest. Keep ties.

<ol start="2">

 <li>Rationale: Sta who maintain every artifact in some collection should be considered favourably in performance reviews.</li>

</ol>

Query: Find all sta         who maintain all artifacts in at least one collection.

<ol start="3">

 <li>Rationale: An artifact collected and maintained by the same sta may have some special requirements that should be investigated.</li>

</ol>

Query: Find all artifacts that were collected by the same sta         who maintains them.

<ol start="4">

 <li>Rationale: Identify multi-talented eld workers.</li>

</ol>

Query: Find all sta       who have collected at least 3 artifacts from every species in some family.

<ol start="5">

 <li>Rationale: Which publications might have some specialized niche focus?</li>

</ol>

Query: Find all publications that have used exactly 2 of our artifacts.

<ol start="6">

 <li>Rationale: Identify motherlode locations.</li>

</ol>

Query: Find all locations where at least one artifact from every family has been collected.

<ol start="7">

 <li>Rationale: Exclusively tissue sample collectors may need extra support for special reagents and shipping costs.</li>

</ol>

Query: Find all sta       who have collected only tissue samples.

<ol start="8">

 <li>Rationale: Collection sta who should be encouraged to diversify their network.</li>

</ol>

Query: Find all sta         pairs who have worked only with each other on collections.

<ol start="9">

 <li>Rationale: Track the in uence of a given sta</li>

</ol>

Query: Sta member SID1 is in uenced by sta member SID2 if (a) they have ever worked together on a collection or (b) if SID1 has ever worked with a sta member who is in uenced by SID2. Find SIDs of sta members in uenced by SID 42.