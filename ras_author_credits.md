<div id="helpdiv"><hr /><h2>ras_author_credits</h2><hr />
<fieldset>
<p><strong>ras_author_credits</strong> returns an href(or not) list of authors with statistics as defined by attribute setting and form values.<br />
<a href="http://images.majyk.net/file_download/6/ras_author_credits_v4.7-dev.txt">Download Link </a><br />
Authors are defined as all users who have posted article data, file uploads, or images for the site. TXP's standard list attributes are supported including section and this_section, also a type attribute is available to discriminate amongst user privileges. <br />
The type attribute's options must match exactly the available choices as
displayed in TXP's user list options, as follows:</p>

<ul><li>Publisher (1)</li>
    <li>Managing Editor (2)</li>
    <li>Copy Editor (3)</li>
    <li>Staff writer (4)</li>
    <li>Freelancer (5)</li>
    <li>Designer (6)</li>
</ul>

<p>Also integer values matching these or custom values can currently be from 0 thru 9. (0 = no privs setting)</p>
<p>The type attribute will accept individual types or integers or a comma delimited list of either or both.</p>
</fieldset>
<hr /><h2>Example (Self Closing)</h2><hr />
<fieldset>
&lt;txp:ras_author_credits break="li" wraptag="ul" type="Publisher,Managing Editor,Copy Editor,7" label="Editors" labeltag="h3" /&gt;
</fieldset>

<fieldset>
<p>Container tag recursive tags and behaviors.</p>
<ul>
<li>&lt;txp:ras_authors /&gt;<br /> : List aware "Author tag" for use inside ras_author_credits (attributes the same as TXP's Author tag).</li>
<li>&lt;txp:ras_users /&gt;<br /> : List aware tag that returns the current user as a tag attribute inside ras_author_credits. (no atts)<br /> : Will return the login name on an author search result page, otherwise it returns unset in a page context outside an author list tag.</li>
</ul>
</fieldset>
<hr /><h2>Example (Container Tag Usage)</h2><hr />
<fieldset>

&lt;txp:ras_author_credits wraptag="ul" break="li"&gt;<br />
&lt;txp:if_author name='&lt;txp:ras_users /&gt;'&gt;-> &lt;/txp:if_author&gt;<br />
			&lt;txp:ras_authors link="1" /&gt;<br />
			&lt;txp:if_author name='&lt;txp:ras_users /&gt;'&gt;<br />
				&lt;txp:article_custom  author='&lt;txp:ras_users /&gt;' wraptag="ul" break="li"&gt;<br />
					&lt;txp:if_article_id&gt;&rsaquo;&lt;/txp:if_article_id&gt;<br />
					&lt;txp:permlink&gt;&lt;txp:title /&gt;&lt;/txp:permlink&gt;<br />
				&lt;/txp:article_custom&gt;<br />
			&lt;/txp:if_author&gt;<br />
		&lt;/txp:ras_author_credits&gt;
</fieldset>

<hr /><h2>Attributes, context &amp; usage.</h2><hr />
<fieldset>
<p> Attributes:</p>
<ul>
			<li>break : Standard TXP attribute. (default is unset)</li>
			<li>label : Standard TXP attribute.</li>
			<li>labeltag : Standard TXP attribute.</li>
			<li>form : Standard TXP attribute.</li>
			<li>wraptag : Standard TXP attribute. (default is unset)</li>
			<li>type : User privilege filters. </li>
			<li>section : Standard TXP attribute. </li>
			<li>this_section : Standard TXP attribute. </li>
			<li>link : Whether or not to link href, 0 no - 1 yes, (Self closing tag only).</li>
			<li>active_only : Show only users that have met select_by criteria, 0 no - 1 yes, default is 1.</li>
			<li>select_by : integer values as set according to a criteria as described in the table below - filters authors by these criterium.</li>
			<li>rank_by : <br /><br />Which content type to use as a ranking criteria (largest number at the top), choices are : "articles - files - images - links" text is not case sensitive but must match exactly one of these four choices. The ranking setting need not match display sets. Three levels of ranking are supported ranked by first to last setting in the comma delimited list.<br /><br /> The sort if only one criteria is set in rank_by is the content type set - then the link text alphabetically. If two or three content types are set, sorting will be by the first to last setting in the comma delimited list. </li>
			<li>class : Standard TXP attribute.</li>
</ul>
</fieldset>
<hr /><h2>Form and Container usage tags.</h2><hr />
<fieldset><p> Return counts for number of posts of the four content types as returned on a per user basis by the following tags when used inside a set of container tags or in a form called by ras_author_credits.</p></fieldset>
<fieldset>
<ul>
<li>&lt;txp:ras_articlecount /&gt; : number of article posts.</li>
<li>&lt;txp:ras_filecount /&gt; : number of uploaded files.</li>
<li>&lt;txp:ras_imagecount /&gt; : number of uploaded images.</li>
<li>&lt;txp:ras_linkcount /&gt; : number of created links.</li>
</ul>
</fieldset>
<fieldset>


<txp:ras_author_credits wraptag="ul" break="li">
<txp:ras_authors link="1" /> - Posts: (<txp:ras_articlecount />) Files: (<txp:ras_filecount />) Images: (<txp:ras_imagecount />)
</txp:ras_author_credits>

<txp:ras_author_credits label="Has posted articles only" labeltag="h3"
rank_by="articles" select_by="5" wraptag="ul" break="li">
<txp:ras_authors link="1" /> - Posts: (<txp:ras_articlecount />)
</txp:ras_author_credits>

<txp:ras_author_credits label="Has uploaded files only" labeltag="h3"
rank_by="files" select_by="5" wraptag="ul" break="li">
<txp:ras_authors link="1" /> - Uploads: (<txp:ras_filecount />)
</txp:ras_author_credits>

<txp:ras_author_credits label="Has posted articles and uploaded files"
labeltag="h3"  rank_by="articles,files" select_by="4" wraptag="ul" break="li">
<txp:ras_authors link="1" /> - Posts: (<txp:ras_articlecount />) | Uploads:
(<txp:ras_filecount />
</txp:ras_author_credits>

</fieldset>
<hr /><h2> Settings list for the "select_by" attribute. </h2><hr />
<fieldset>

<table cellpadding="2" cellspacing="1" border="1px">
							<tr><td> 1 </td><td> select if an article has been posted </td></tr>
							<tr><td> 2 </td><td> select if a file has been uploaded </td></tr>
							<tr><td> 3 </td><td> select if an article has been posted or a file uploaded </td></tr>
							<tr><td> 4 </td><td> select if an article has been posted and a file uploaded </td></tr>
							<tr><td> 5 </td><td> select if an article has been posted and a file has not been uploaded</td></tr>
							<tr><td> 6 </td><td> select if a file has been uploaded and an article has not been posted </td></tr>
							<tr><td> 7 </td><td> select if an image has been uploaded </td></tr>
							<tr><td> 8 </td><td> select if an image or a file has been uploaded </td></tr>
							<tr><td> 9 </td><td> select if an image and a file have been uploaded </td></tr>
							<tr><td> 10 </td><td> select if an image has been uploaded and a file has not been uploaded </td></tr>
							<tr><td> 11 </td><td> select if a file has been uploaded and an image has not been uploaded </td></tr>
							<tr><td> 12 </td><td> select if an article has been posted or an image uploaded </td></tr>
							<tr><td> 13 </td><td> select if an article has been posted and an image uploaded </td></tr>
							<tr><td> 14 </td><td> select if an article has been posted and an image has not been uploaded </td></tr>
							<tr><td> 15 </td><td> select if an article has not been posted and an image has been uploaded </td></tr>
							<tr><td> 16 </td><td> select if an article has been posted or an image uploaded or a file uploaded </td></tr>
							<tr><td> 17 &nbsp;</td><td> select if an article has been posted and an image uploaded and a file uploaded </td></tr>
							</table>
</fieldset>
</div>
