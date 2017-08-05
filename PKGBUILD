# Maintainer: Eric Vidal <eric@obarun.org>


pkgname=obarun-mkiso
_commit=38fe127cdcee1d1fe388ce02837b657fb5478ea8 # tag v0.0.7
pkgver=0.0.7
pkgrel=1
pkgdesc=" Script for making an iso"
arch=(x86_64)
url="https://github.com/Obarun/obarun-mkiso"
license=('BEERWARE')
depends=('git' 'pacman' 'obarun-libs' 'squashfs-tools' 'libisoburn' 'gzip' 'archiso' 'syslinux')
makedepends=('git')
backup=('etc/obarun/mkiso.conf')
install=
#source=("obarun-mkiso::git+https://github.com/Obarun/obarun-mkiso#tag=v${pkgver}")
source=("git+https://github.com/Obarun/obarun-mkiso#commit=$_commit")
md5sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

package() {
	cd "$srcdir/$pkgname"

	install -Dm 0755 "obarun-mkiso.in" "$pkgdir/usr/bin/obarun-mkiso"
	install -Dm 0755 "mkiso.sh" "$pkgdir/usr/lib/obarun/mkiso.sh"
	install -dm 0755 "$pkgdir/usr/lib/obarun/mkiso/"
	install -Dm 0755 "mkiso/build.sh" "$pkgdir/usr/lib/obarun/mkiso/build.sh"
	install -Dm 0755 "mkiso/make.sh" "$pkgdir/usr/lib/obarun/mkiso/make.sh"
	install -Dm 0644 "mkiso.conf" "$pkgdir/etc/obarun/mkiso.conf"
	install -dm 0755 "$pkgdir/usr/share/licenses/obarun-mkiso/"
	install -Dm 0644 "LICENSE" "$pkgdir/usr/share/licenses/obarun-mkiso/LICENSE"
	install -Dm 0644 "PKGBUILD" "$pkgdir/var/lib/obarun/obarun-mkiso/update_package/PKGBUILD"
	
	install -dm 0755 "$pkgdir/var/lib/obarun/obarun-mkiso"
	install -Dm 0644 "mkinitcpio.conf" "$pkgdir/var/lib/obarun/obarun-mkiso/mkinitcpio.conf"
	install -Dm 0644 "pacman.conf" "$pkgdir/var/lib/obarun/obarun-mkiso/pacman.conf"
	
	for d in efiboot isolinux syslinux; do
		cp -aT "${d}" "$pkgdir/var/lib/obarun/obarun-mkiso/${d}"
	done
}
