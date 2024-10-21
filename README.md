<h1>File Permissions</h1>

### [YouTube Demonstration](https://youtu.be/your_youtube_link_here)

<h2>Description</h2>

<h2>Project Overview</h2>
    <p>This project involves reviewing and managing file permissions on a Linux system as the user <code>researcher2</code>. It covers essential Linux commands to view and modify permissions for users, groups, and others.</p>
<h2>Viewing File Permissions</h2>
<p align="center">
<img src="https://i.imgur.com/MckXSWj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>To begin, the <code>ls</code> command is utilized to view directories and files under the projects directory. The command <code>ls -l</code> provides a detailed list of the contents, including permissions. For instance, in the <code>/home/researcher2/projects</code> directory, the following files and their permissions are present:</p>

<ul>
      <li><strong>project_k.txt</strong>
            <ul>
                <li>User: read, write</li>
                <li>Group: read, write</li>
                <li>Other: read, write</li>
            </ul>
        </li>
        <li><strong>project_m.txt</strong>
            <ul>
                <li>User: read, write</li>
                <li>Group: read</li>
                <li>Other: none</li>
            </ul>
        </li>
        <li><strong>project_r.txt</strong>
            <ul>
                <li>User: read, write</li>
                <li>Group: read, write</li>
                <li>Other: read</li>
            </ul>
        </li>
        <li><strong>project_t.txt</strong>
            <ul>
                <li>User: read, write</li>
                <li>Group: read, write</li>
                <li>Other: read</li>
            </ul>
        </li>
    </ul>

<h2>Understanding Permission Strings</h2>
    <p>Permissions are represented in a 10-character string format. The breakdown is as follows:</p>
    <ul>
        <li>The first character indicates the type (d for directory).</li>
        <li>The next three characters denote the User's permissions (read, write, execute).</li>
        <li>The following three characters represent the Group's permissions.</li>
        <li>The last three characters signify Others' permissions.</li>
    </ul>
    <p>For example, the string <code>-rw-r-----</code> for <code>project_m.txt</code> indicates it is a file (not a directory) with:</p>
    <ul>
        <li>User: read, write</li>
        <li>Group: read</li>
        <li>Others: none</li>
    </ul>

<h2>Modifying File Permissions</h2>
    <p>To adhere to organizational policy, we need to restrict write permissions for Others. For example, to remove write permissions for <code>project_k.txt</code>, the command used is:</p>
    <pre><code>chmod o-w project_k.txt</code></pre>

<h3>Changing Permissions on a Hidden File</h3>
<p align="center">
<img src="https://i.imgur.com/uUC44yJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
    <p>Hidden files can be viewed with <code>ls -la</code>. The research team has archived <code>.project_x.txt</code>, which is a hidden file. It should not allow write permissions for any user. Initially, both the user and group have write permissions. We can modify the permissions using:</p>
    <pre><code>chmod u=r,g=r .project_x.txt</code></pre>
    <p>This command ensures only read permissions are granted to the user and group, resulting in:</p>
    <ul>
        <li>User: read</li>
        <li>Group: read</li>
    </ul>
<p align="center">
<img src="https://i.imgur.com/1FJB8g9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h3>Changing Directory Permissions</h3>
<p align="center">
<img src="https://i.imgur.com/sNjcIUi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
    <p>The organization requires that only <code>researcher2</code> has access to the <code>drafts</code> directory and its contents. To achieve this, the following commands are executed:</p>
    <pre><code>chmod g-x .</code></pre>
    <pre><code>chmod g-r,g-x,o-r,o-x ..</code></pre>
    <p>These commands effectively eliminate group and others' permissions, ensuring only the user retains access.</p>
<p align="center">
<img src="https://i.imgur.com/qRrCRoR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<h2>Summary</h2>
    <p>The primary objective of managing file permissions is to prevent unauthorized access, aligning with the principle of least privilege. This concept dictates that users should only have access to the data and resources necessary to perform their tasks. Throughout this activity, permissions have been reviewed and modified using the <code>ls -la</code> and <code>chmod</code> commands, reinforcing the importance of secure file management in Linux.</p>
