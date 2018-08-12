## Google Compute Engine: how to set hostname permanently?

<div class="post-text" itemprop="text">
<ol>
<li>Click EDIT on your instance</li>
<li>Go to "Custom metadata" section</li>
<li>Add  <code>hostname</code> + <code>your.hostname.tld</code> (change "your.hostname.tld" to your actual hostname</li>
<li>run <code>curl --silent "http://metadata.google.internal/computeMetadata/v1/instance/attributes/hostname" -H "Metadata-Flavor: Google"</code></li>
<li>run <code>sudo env EDITOR=nano crontab -e</code> to edit crontab</li>
<li>add line <code>@reboot hostname $(curl --silent "http://metadata.google.internal/computeMetadata/v1/instance/attributes/hostname" -H "Metadata-Flavor: Google")</code></li>
<li>On your keyboard <code>Ctrl</code> + <code>X</code></li>
<li>On your keyboard hit <code>Y</code></li>
<li>On your keyboard hit <code>Enter</code></li>
<li>run <code>reboot</code></li>
<li>after system rebooted, run <code>hostname</code> and see if your changes applied</li>
</ol>

<p>Good luck!</p>
    </div>
<hr>
Source: <a href="https://stackoverflow.com/a/48151928">Stack Overflow</a>
