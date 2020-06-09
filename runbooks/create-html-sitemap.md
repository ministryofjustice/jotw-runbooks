---
category: Runbooks
expires: 2021-01-31
---

# Create an HTML sitemap from an .xml file

## Required

* You need to have the XML file
* You need to be running PHP on your computer

## Instructions

1. Copy the below code snippet and add it to a new PHP file.
2. Populate the fields in the code with your own configuration details.
3. run `php <name of php file>`.

This code is also available to download at
* [create-html-sitemap.php](https://github.com/ministryofjustice/justice-on-the-web/blob/master/code_snippets/create-html-sitemap.php)

```
<?php
/**
 * Takes an XML site map and creates an HTML table full of links.c
 * Used to aid creation of the justice.gov.uk (mirror) site map.
 *
 * What now?
 * - Put the XML file and this script on a server running PHP7
 * - Give the vars below some data
 * - - $site_map = site map path relative to this script
 * - - $root_domain = main domain of the website including URL protocol
 * - - $highlights = an optional array of text (keys) and colour (values)
 * - Load the script in your browser
 * - Copy the source code and use at will
 *
 * @link http://justice.gov.uk.s3-website-eu-west-1.amazonaws.com/sitemap.html
 * @author Damien Wilson
 */
// path to the site map xml file
$site_map = 'site-map.xml';
// domain stated here will be removed from display - leave empty to keep
$root_domain = 'http://justice.gov.uk.s3-website-eu-west-1.amazonaws.com/';
/**
 * Wrap some text in => colour
 */
$highlights = [
    'procedure-rules' => 'green',
    'civil' => '#ff8f22',
    'criminal' => '#ff4aec',
    'family' => '#5060ff'
];
/***********************************************************/
/*** Process the XML ***/
$dom = new DomDocument();
$dom->load($site_map);
$data = $dom->getElementsByTagName('loc');
$rows = '';
foreach ($data as $node) {
    $url = $node->textContent;
    $rows .= '<tr><td><a href="' . $url . '">' . format_display_url($url) . '</a></td></tr>';
}
/***********************************************************/
/*** Output the HTML ***/
echo '<!doctype html>';
echo '<html>';
echo '<head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /></head>';
echo '<body><table>' . $rows . '</table></body>';
echo '</html>';
// Helper functions
/**
 * @param $url
 * @return string
 */
function format_display_url($url): string
{
    global $root_domain;
    $a = [
        'search' => [
            rtrim($root_domain, '/'),
            '/' // blow apart
        ],
        'replace' => [
            '',
            '&nbsp;/&nbsp;'
        ]
    ];
    $a = maybe_add_custom_formats($a);
    return str_replace($a['search'], $a['replace'], $url);
}
/**
 * @param $a
 * @return array
 */
function maybe_add_custom_formats($a): array
{
    global $highlights;
    // text highlighting
    if (is_array($highlights) && !empty($highlights)) {
        foreach ($highlights as $text => $colour) {
            $a['search'][] = $text;
            $a['replace'][] = "<strong style='color:" . $colour . "'>" . $text . "</strong>";
        }
    }
    return $a;
}
```