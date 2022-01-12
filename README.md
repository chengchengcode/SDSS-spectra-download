# SDSS-spectra-download

I tried to download the SDSS spectrum from XID by astroquery:

astroquery.sdss.get_spectra(matches=xid)

I cannot get the data when the 'instrument' in XID is BOSS.

Then I found the astroquery.sdss only know SDSS, EBOSS or some other names.

So I change the instrument name manually from BOSS to EBOSS:

xid = astroquery.sdss.query_region(pos, spectro=True)

xid.remove_column('instrument')

xid.add_column(name='instrument', col=['EBOSS'])

sp = SDSS.get_spectra(matches=xid)

Then the download works.
