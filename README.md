# Download League of Legends Data Dragon
[![Daily Test (@v1)](https://github.com/mikaeldui/download-league-of-legends-data-dragon/actions/workflows/daily-test.v1.yml/badge.svg)](https://github.com/mikaeldui/download-league-of-legends-data-dragon/actions/workflows/daily-test.v1.yml)

![image](https://user-images.githubusercontent.com/3706841/149832547-f691560f-94ce-4bf9-b276-4afce6279c3a.png)

A GitHub Action for downloading the League of Legends Data Dragon. The download takes ~5 seconds.

> Data Dragon is our way of centralizing League of Legends game data and assets, including champions, items, runes, summoner spells, and profile icons. All of which can be used by third-party developers. You can download a compressed tarball (.tgz) for each patch which will contain all assets for that patch. Please be aware that updating Data Dragon after each League of Legends patch is a manual process, so it is not always updated immediately after a patch. - [Riot Developer Portal](https://developer.riotgames.com/docs/lol#data-dragon)

## Example
Download the latest version as `./dragontail.tgz` *([or `./dragontail.zip` if the version is a zip](https://developer.riotgames.com/docs/lol#:~:text=Patch%2010.10%20was%20uploaded%20as%20a%20zip%20archive%20(.zip)%20instead%20of%20the%20typical%20compressed%20tarball%20(.tgz)))*.

    - name: Download Data Dragon
      uses: mikaeldui/download-league-of-legends-data-dragon@v1
      
    - name: Extract Data Dragon
      run: tar -xvzf dragontail.tgz
      
## Inputs
### `region`
> Data Dragon versions aren't always equivalent to the League of Legends client version in a region. - [Riot Developer Portal](https://developer.riotgames.com/docs/lol#:~:text=Data%20Dragon%20versions%20aren%27t%20always%20equivalent%20to%20the%20League%20of%20Legends%20client%20version%20in%20a%20region.%20You%20can%20find%20the%20version%20each%20region%20is%20using%20via%20the%20realms%20files.)

    - name: Download Data Dragon for EUW
      uses: mikaeldui/download-league-of-legends-data-dragon@v1
      with:
        region: EUW
        
### `version`
Can't be used together with `region`. Download a specific version of the Data Dragon.

    - name: Download Data Dragon version 12.1.1
      uses: mikaeldui/download-league-of-legends-data-dragon@v1
      with:
        version: 12.1.1     
        
### `path`
You can set a custom path for the downloaded file. The default is `./dragontail.tgz`.

*Note: version 10.10 was a .zip and if a zip is downloaded the extension will be changed to .zip, even for a custom path.*

    - name: Download Data Dragon version 12.1.1
      uses: mikaeldui/download-league-of-legends-data-dragon@v1
      with:
        region: EUW
        path: './dragontails/euw.tgz'
        
### Outputs

#### `version`
The action will output the version of the Data Dragon downloaded.

    - name: Download Data Dragon
      uses: mikaeldui/download-league-of-legends-data-dragon@v1
      id: data-dragon
      
    - name: Print the version
      run: echo "Downloaded Data Dragon version: ${{ steps.data-dragon.outputs.version }}"

#### `path`
[Version 10.10 was a zip](https://developer.riotgames.com/docs/lol#:~:text=Patch%2010.10%20was%20uploaded%20as%20a%20zip%20archive%20(.zip)%20instead%20of%20the%20typical%20compressed%20tarball%20(.tgz)). If the downloaded Data Dragon is a zip the extension will be changed to zip. This also applies if you specify a manual path ending with ".tgz". You can get the path to the file written from the action output.

    - name: Download Data Dragon
      id: data-dragon
      uses: mikaeldui/download-league-of-legends-data-dragon@v1
      
    - name: Extract Data Dragon
      run: tar -xvzf ${{ steps.data-dragon.outputs.path }}
        
## Notice from Riot Games, Inc.
The GitHub Action "[Download League of Legends Data Dragon](https://github.com/marketplace/actions/download-league-of-legends-data-dragon)" by [@mikaeldui](https://github.com/mikaeldui) isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing Riot Games properties. Riot Games, and all associated properties are trademarks or registered trademarks of Riot Games, Inc.
