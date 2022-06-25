# syntax=docker/dockerfile:1

FROM archlinux
RUN echo 'Server = http://ftp.byfly.by/pub/archlinux/$repo/os/$arch' > /etc/pacman.d/mirrorlist
RUN echo 'Server = http://mirror.datacenter.by/pub/archlinux/$repo/os/$arch' > /etc/pacman.d/mirrorlist
RUN pacman -Syyu --noconfirm
RUN pacman-db-upgrade
RUN pacman -S maxima-ecl --noconfirm
RUN pacman -S jupyter-notebook --noconfirm
RUN pacman -S sagemath --noconfirm
RUN pacman -S doas --noconfirm
RUN pacman -S python-pip --noconfirm
RUN pacman -S python-frozendict --noconfirm
RUN pacman -Scc --noconfirm
RUN echo permit nopass :root > /etc/doas.conf
RUN echo 'root:'$(date +%s | sha256sum | base64 | head -c64) | chpasswd
RUN echo 'root:'$(</dev/random head -c2048 | sha256sum | base64 | head -c64) | chpasswd
ADD entrypoint /usr/bin/entrypoint
ENTRYPOINT ["entrypoint"]

CMD cd Desktop && jupyter notebook  --NotebookApp.token='' --NotebookApp.password='' --port=8080 --ip 0.0.0.0
