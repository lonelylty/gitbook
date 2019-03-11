download nuget client

https://www.nuget.org/downloads

regeister nuget api key

https://www.nuget.org/account/apikeys

	nuget setApiKey <api_key> oy2ao6iij3z23hphibhatkbqdliwyqee5opksklgtckr2i
	
	nuget spec
	
	nuget pack <proj_name> -Prop Configuration=Release
	
	nuget push <pack_name> -NonInteractive -Source https://www.nuget.org/api/v2/package


tips:

.nuspec file format

<license type="expression">MIT</license>

sysdm.cpl

<ItemGroup>
    <EmbeddedResource Include="wkhtmltoimage.exe">
      <IncludeInPackage>true</IncludeInPackage>
    </EmbeddedResource>
</ItemGroup>