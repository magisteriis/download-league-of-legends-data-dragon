# Download Data Dragon
[![Daily Test (@main)](https://github.com/mikaeldui/download-data-dragon/actions/workflows/daily-test.main.yml/badge.svg)](https://github.com/mikaeldui/download-data-dragon/actions/workflows/daily-test.main.yml)

![image](https://user-images.githubusercontent.com/3706841/149832547-f691560f-94ce-4bf9-b276-4afce6279c3a.png)

A GitHub Action for downloading the League of Legends Data Dragon.

> Data Dragon is our way of centralizing League of Legends game data and assets, including champions, items, runes, summoner spells, and profile icons. All of which can be used by third-party developers. You can download a compressed tarball (.tgz) for each patch which will contain all assets for that patch. Please be aware that updating Data Dragon after each League of Legends patch is a manual process, so it is not always updated immediately after a patch. - [Riot Developer Portal](https://developer.riotgames.com/docs/lol#:~:text=tier%2Dicons.zip-,Data%20Dragon,-Data%20Dragon%20is)

## Example
If you don't specify any inputs the latest version will be downloaded as "dragontail.tgz" (or "dragontail.zip" if the [version is a zip](https://developer.riotgames.com/docs/lol#:~:text=Patch%2010.10%20was%20uploaded%20as%20a%20zip%20archive%20(.zip)%20instead%20of%20the%20typical%20compressed%20tarball%20(.tgz))).

    - name: Download Data Dragon
      uses: mikaeldui/download-data-dragon@v1
      
### Regions
> Data Dragon versions aren't always equivalent to the League of Legends client version in a region. You can find the version each region is using via the realms files. - [Riot Developer Portal](https://developer.riotgames.com/docs/lol#:~:text=Data%20Dragon%20versions%20aren%27t%20always%20equivalent%20to%20the%20League%20of%20Legends%20client%20version%20in%20a%20region.%20You%20can%20find%20the%20version%20each%20region%20is%20using%20via%20the%20realms%20files.)

    - name: Download Data Dragon for EUW
      uses: mikaeldui/download-data-dragon@v1
      with:
        region: EUW
        
### Specific version
Can't be used together with `region`.

    - name: Download Data Dragon version 12.1.1
      uses: mikaeldui/download-data-dragon@v1
      with:
        version: 12.1.1     
        
### Path
You can set a custom path for the downloaded file. The default is 'dragontail.tgz'.

    - name: Download Data Dragon version 12.1.1
      uses: mikaeldui/download-data-dragon@v1
      with:
        version: 12.1.1
        path: './dragontails/12.1.1.tgz'
        
### Outputs
[Version 10.10 was a zip](https://developer.riotgames.com/docs/lol#:~:text=Patch%2010.10%20was%20uploaded%20as%20a%20zip%20archive%20(.zip)%20instead%20of%20the%20typical%20compressed%20tarball%20(.tgz)). If the downloaded Data Dragon is a zip the extension will be changed to zip. This also applies if you specify a manual path ending with ".tgz". You can get the path to the file written from the action output.

    - name: Download Data Dragon
      id: data-dragon
      uses: mikaeldui/download-data-dragon@v1
      
    - name: Extract Data Dragon
      run: tar -xvzf ${{ steps.data-dragon.outputs.path }}
        
## Notice from Riot Games, Inc.
The GitHub Action "Download Data Dragon" by @mikaeldui isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing Riot Games properties. Riot Games, and all associated properties are trademarks or registered trademarks of Riot Games, Inc.
