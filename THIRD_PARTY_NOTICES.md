# Third-party notices

NucSyn 0.1.2 is distributed as a container image. The image includes third-party
software that remains subject to its own license terms. Those terms govern those
components; the NucSyn Academic Research License does not alter them.

Authoritative third-party license texts are shipped **inside the container
image**. After loading the image you can read them at:

```text
/opt/nucsyn/licenses/forna/FORNA-LICENSE.txt    forna (fornac) upstream license
/opt/nucsyn/licenses/forna/upstream.tsv         forna upstream version/commit/archive hash
/opt/nucsyn/licenses/forna/node-packages.tsv    renderer npm packages and versions
/opt/nucsyn/licenses/forna/packages/            per-package license files
/opt/nucsyn/licenses/node/NODE-LICENSE.txt      Node.js license
```

The Python runtime and its dependencies are installed with their own distributed
metadata and license files under the image's `site-packages`.

## Components distributed inside the image

| Component | Role | Notes |
|---|---|---|
| Ubuntu base image | Base operating system layer | Canonical; individual packages under their own licenses |
| CPython 3.11 | Python runtime | PSF License |
| ViennaRNA | RNA secondary-structure folding, partition function, energy evaluation | Upstream ViennaRNA license terms |
| Turner 1999 energy parameters | Nearest-neighbour thermodynamic parameter set | Distributed as a data file with the Core package |
| forna / fornac | Structure rendering for the optional switch-MFE report | Stock upstream 1.2.0, commit `99be5d18e34637e67d24d58e9bad5c1a5e3f133d`, fetched by verified SHA-256; unmodified |
| Node.js | Runtime for the forna renderer | Unmodified Node.js binary from the official `node:22-bookworm-slim` image, pinned by digest (recorded in the companion manifest); Node.js license |
| npm packages used by the renderer | Renderer dependencies | Enumerated with versions in `node-packages.tsv` |
| NumPy, SciPy, pandas, matplotlib, networkx, Biopython, pydantic, PyYAML, python-dotenv, multiprocess, reportlab | Python dependencies of the Core package | Each under its own license, mostly BSD/MIT/Apache-2.0-style; see installed package metadata |

## Software NOT distributed with NucSyn

The following are **not** included in the bundle or in the image, are **not**
redistributed by this project, and are **not** licensed to you by us. You must
obtain them yourself and comply with their own terms.

| Component | Why it is needed | Your responsibility |
|---|---|---|
| **RNAaccess** (`run_raccess`) | Accessibility computation used by the trigger-selection workflows | Separately licensed third-party software. Obtain it from its authors under their terms, then bind-mount it into the container as documented. NucSyn contains no RNAaccess binary, source, vendored copy or hash. |
| **NCBI BLAST+** (`blastn`, `makeblastdb`) | Only for the optional off-target screen | Obtain from NCBI under its terms. |
| **Reference sequence databases** | Only for the optional off-target screen | NucSyn never downloads or builds a reference database. You select the organism/transcriptome data, you build the BLAST database, and you are responsible for the data's license and terms of use. |

## Trademarks

Product and organization names mentioned here are used only to identify the
software concerned, and remain the property of their respective owners. Their
mention does not imply endorsement of NucSyn.

## Corrections

If you believe a component is attributed incorrectly or a required notice is
missing, please contact:

> Prof. Tamir Tuller — <tamirtul@post.tau.ac.il>
