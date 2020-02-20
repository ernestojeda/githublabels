stage 'init'
    node {
        stage ('Checkoutscm') {
            scmCheckout {
                clean = true
                }
        stage ('execute shell') {
            sh '''
                bash github-copy-labels.sh $GH_TOKEN $SRC_GH_USER $SRC_GH_REPO $TGT_GH_USER $TGT_GH_REPO
            '''
                 }
}
